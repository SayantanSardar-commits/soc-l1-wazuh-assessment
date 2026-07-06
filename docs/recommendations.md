# Recommendations — Path to Level 4+ SOC Maturity

Current maturity: **Level 3 / 5**

## 1. Immediate (Week 1)
- Tune alerts: whitelist SCA scans, PowerShell temp patterns, Update-folder drops
- Build detection runbooks & SOC triage training
- **Expected impact:** 26% fewer false positives, 50% faster triage

## 2. Short-term (1–4 weeks)
- Deploy network IDS (Suricata) for WinRM/SMB anomaly detection
- Evaluate & deploy an EDR platform; integrate telemetry with Wazuh
- **Estimated cost:** $20K–35K
- **Benefit:** improved reconnaissance & behavioral visibility

## 3. Long-term (3–6 months)
- Establish 24/7 SOC staffing (2+ additional FTE)
- Deploy ML-based malware detection & a formal threat hunting program
- **Estimated cost:** $150K–200K annually
- **Benefit:** real-time incident response capability

---

**Final recommendation:** Proceed with immediate alert tuning now; begin procurement planning for network IDS and EDR platforms in parallel.
