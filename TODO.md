# Blue Team Portfolio - TODO

## Current Project: 01 - Deception-Based Detection Lab (Wazuh + auditd)

### Technical work - DONE
- [x] Lab setup: Wazuh SIEM + agent Active, single-adapter/static-IP fix
- [x] Plant AWS credentials honeytoken + persistent auditd read-watch
- [x] Wazuh rule 100300 (alert) + 100301 (self-scan suppression)
- [x] Validate with wazuh-logtest (cat fires, syscheckd suppressed)
- [x] Live attack: reverse shell → credential sweep → alert (MITRE T1552.001)
- [x] Docs: explainer, technical log, ADS-001 detection design
- [x] Capture evidence screenshots

### Publishing - TO DO
- [ ] Fix screenshot filenames with doubled `.png.png` extensions
- [ ] Build GitHub repo structure (README, docs/, detections/, attack/, evidence/)
- [ ] Write README (lead with the money-shot alert; keep the lessons-learned section)
- [ ] Draft + publish the LinkedIn post
- [ ] Push to GitHub

### Optional extensions (nice-to-have)
- [ ] Sigma rule version of ADS-001
- [ ] Detection-as-code CI (GitHub Actions: `wazuh-analysisd -t` on push)
- [ ] Second honeytoken - SSH-key canary → ADS-002
- [ ] MITRE ATT&CK Navigator coverage heatmap + gap analysis

## Per-project checklist (repeat for future projects)
- [ ] Setup / telemetry in place
- [ ] Detection content written + validated
- [ ] Attack simulation proves the detection
- [ ] Evidence screenshots captured
- [ ] Write-up + LinkedIn post drafted
- [ ] Pushed to GitHub
