# MITRE ATT&CK Coverage

**9 / 14 techniques detected (64%)** across **5 / 5 major tactics**.

| Tactic | Technique(s) | Rule IDs |
|---|---|---|
| Execution (T1059) | PowerShell · Windows Command Shell | 92201, 92033, 92052 |
| Lateral Movement (T1021) | T1021.006 Remote Services (WinRM) | 92657 |
| Privilege Escalation (T1548) | T1548.002 Token Impersonation | 67028, 61640 |
| Persistence (T1053 / T1547) | Scheduled Task · Active Setup | 92307, 61104 |
| Discovery (T1087 / T1007) | Account Discovery · Service Discovery | 92039, 92033 |

**Assessment:** Excellent coverage of execution and lateral movement tactics.

**Gap / recommendation:** Expand persistence detection to cover registry run keys, WMI event subscriptions, and DLL injection — these are common real-world persistence techniques not exercised in this simulation.
