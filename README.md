# Blue Team Portfolio - Detection Engineering

Hands-on defensive security projects that mirror the real day-to-day work of a
SOC analyst and detection engineer: planting telemetry, writing and tuning
detections, simulating attacks, and validating that alerts fire cleanly against
a live intrusion.

The focus is detection content, investigative tradecraft, and honest
engineering - real troubleshooting captured as it happened, not a polished
fiction.

Each project is a self-contained case study combining:
- **Lab build / setup** - the environment and data sources
- **Detection engineering** - the rules and suppression logic written for it
- **Attack simulation** - an adversary emulation that proves the detection
- **Evidence** - screenshots of the work end to end

---

## Projects

| # | Project | Platform | Focus | Status |
|---|---------|----------|-------|--------|
| 01 | [Deception-Based Detection Lab](./deception-detection-lab/) | Wazuh + auditd | Honeytoken detection engineering | Built - publish pending |

**Deception-Based Detection Lab** - a detection layer with a near-zero
false-positive rate, not by tuning but by design. A fake AWS credentials file
(a honeytoken) is planted on a Linux host; any access to it is, by construction,
an intruder. Built on a 4-VM lab (Wazuh SIEM, Ubuntu target, Kali attacker,
analyst workstation) with `auditd` for read-level detection and custom Wazuh
rules - including a suppression rule so the system never alerts on itself. Proven
against a live reverse-shell + credential-sweep attack, mapped to MITRE ATT&CK
T1552.001. See [`HANDOVER.md`](./deception-detection-lab/HANDOVER.md) for the
full write-up.

---

## Skills demonstrated

Deception engineering · Wazuh SIEM · custom detection rules · false-positive
suppression · Linux auditd · adversary emulation · MITRE ATT&CK · incident
evidence

## Disclaimer

All work is performed in an isolated home lab for **educational purposes** and
**authorized defensive security use only**. All credentials used as bait are
fake; attack simulation is run only against the operator's own lab hosts.
