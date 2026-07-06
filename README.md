# SOC L1 — Wazuh EDR/SIEM Capability Assessment

A multi-stage attack simulation and detection analysis against a Wazuh-based SIEM deployment, evaluating real-world detection coverage across a full attack chain on a Windows 10 endpoint.

**Report ID:** SAT-2026-0705-001
**Assessment Date:** July 4–5, 2026
**Platform:** Wazuh v4.14.6 SIEM
**Classification:** Internal Use Only

---

## TL;DR

| Metric | Result |
|---|---|
| Correlated events (24h) | 1,164 |
| Attack phase coverage | 100% (5/5 phases) |
| Alert latency | < 1 sec |
| MITRE tactics detected | 5 / 5 |
| MITRE techniques detected | 9 / 14 (64%) |
| False positive rate | 26% (mostly compliance scanning) |
| Current SIEM maturity | Level 3 / 5 |
| Overall risk | LOW (with recommended enhancements) |

---

## Environment

Three-node simulation lab:

| Node | Role | Specs |
|---|---|---|
| SIEM Manager | Ubuntu 20.04 LTS · 192.168.0.102 | Wazuh v4.14.6 · 4 vCPU / 8GB RAM |
| Target Endpoint | Windows 10 Home · 192.168.0.103 | Build 19045.2965 · 2 vCPU / 4GB RAM |
| Attack Platform | Kali Linux 2026.2 · 192.168.0.104 | Metasploit, CrackMapExec, Nmap |

**Threat model scope:**
- Credential-based initial access (valid account exploitation)
- Remote code execution via management protocols
- Privilege escalation via token manipulation
- Persistence via scheduled task creation
- Discovery & lateral movement

---

## Repo structure

​```
soc-l1-wazuh-assessment/
├── README.md                     # this file
├── attack-timeline.md            # phase-by-phase attack chain
├── mitre-attack-mapping.md       # MITRE ATT&CK coverage table
├── recommendations.md            # phased roadmap to Level 4+ SOC maturity
└── SOC_l1_WAZUH.pdf              # original full report
​```

See `attack-timeline.md`, `mitre-attack-mapping.md`, and `recommendations.md` for the detailed breakdown, or `SOC_l1_WAZUH.pdf` for the full assessment as presented.


## Key findings

- Real-time alert generation at sub-second latency
- Effective parent-child process chain correlation
- Complete forensic artifact preservation & timeline reconstruction
- False positive rate of 26%, primarily from compliance scanning noise
- Overall risk rated **LOW**, contingent on recommended tuning/enhancements

## Conclusion

The SIEM demonstrated complete detection coverage across all five simulated MITRE ATT&CK tactics, with sub-second alerting and multi-source correlation exceeding 90% confidence. Recommended next steps: immediate alert tuning, followed by procurement of network IDS and EDR platforms, and eventually 24/7 SOC staffing.

---

*Report generated July 5, 2026. Classification: Internal Use Only — review before making this repo public if it contains anything sensitive to your organization.*
