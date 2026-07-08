# Blue Team Portfolio - Progress

## Status Legend
- `[ ]` Not started
- `[~]` In progress
- `[x]` Complete

Defensive security case studies that mirror real detection-engineer work.
Each project = setup + detection content + attack simulation + evidence,
written up for GitHub and LinkedIn.

---

## Project 01: Deception-Based Detection Lab
**Status:** [~] Built and validated - publishing pending
**Platform:** Wazuh SIEM + auditd (4-VM lab: Wazuh server, Ubuntu target, Kali attacker, analyst workstation)
**Thesis:** A detection with a near-zero false-positive rate by design - a
honeytoken no legitimate user touches, so any access IS the intrusion.

### Done
- [x] Phase 1 - Lab setup & connectivity (single-adapter fix, static SIEM IP, agent Active)
- [x] Phase 2 - AWS credentials honeytoken planted + persistent auditd read-watch
- [x] Phase 3 - Wazuh rule 100300 (level 12 alert) + rule 100301 (self-scan suppression), validated via wazuh-logtest
- [x] Phase 4 - Live attack: Kali reverse shell → recon → credential sweep fires the alert (MITRE T1552.001)
- [x] Documentation: explainer doc, technical log, ADS-001 detection design doc
- [x] Evidence screenshots captured (agent, bait, audit event, live alert, attack chain)

### Pending
- [ ] Rename screenshots with doubled `.png.png` extensions
- [ ] Build the GitHub repo structure (README, detections/, attack/, evidence/)
- [ ] Write and publish the LinkedIn post (lead with the money-shot alert)
- [ ] Optional: Sigma rule version of ADS-001
- [ ] Optional: detection-as-code CI (GitHub Actions running `wazuh-analysisd -t`)
- [ ] Optional: second honeytoken (SSH-key canary → ADS-002)
- [ ] Optional: MITRE ATT&CK Navigator coverage heatmap

---

## Session Log
| Date | Project | What was done |
|------|---------|---------------|
| 2026-07-01 | Setup | Created blue-team-portfolio repo (separate from the offensive portfolio) for realistic SOC/detection-engineer case studies, written up for LinkedIn |
| 2026-07-08 | Deception Detection Lab | Consolidated the portfolio onto the one real, validated project - the Wazuh honeytoken deception lab (Phases 1-4 complete, proven against a live attack). Removed the earlier empty Splunk project scaffolds. Moved the lab (9 screenshots + HANDOVER.md) into `deception-detection-lab/`. Publishing to GitHub + LinkedIn still pending |
