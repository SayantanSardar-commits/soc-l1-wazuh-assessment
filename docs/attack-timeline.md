# Attack Timeline

Five-phase attack chain, all phases detected by Wazuh.

## Phase 1 — Reconnaissance (9 min)
- Nmap service scan against target endpoint
- WinRM (port 5985) found open
- Host confirmed patched against EternalBlue

## Phase 2 — Credential Access (15 min)
- Valid-account WinRM authentication over NTLM
- **Detection:** Rule 92657 — Successful Remote Logon
  - Severity: Level 6
  - Latency: < 1 second

## Phase 3 — Remote Code Execution (60 sec)
- Metasploit `winrm_script_exec` module delivered a payload via the authenticated WinRM session to a Temp directory
- **Detections:**
  - Rule 92213 — Executable dropped in malware-linked folder (Level 15, ×16)
  - Rule 92052 — Command prompt started by abnormal process (Level 4, ×190)
  - Rule 92201 — PowerShell created scripting file in temp (Level 9, ×17)
- Total correlated alerts: 240+
- Detection effectiveness: Excellent

## Phase 4 — Privilege Escalation (5 sec)
- Process migrated to `svchost.exe` under the SYSTEM context
- `SeTcbPrivilege` assigned to the compromised account
- **Detection:** Rule 67028 — Special privileges assigned
  - Latency: 5 seconds

## Phase 5 — Persistence (30 sec)
- Scheduled task created to execute `cmd.exe` under SYSTEM at every logon:

  ```
  schtasks /create /sc onlogon /tn "WindowsUpdate" /tr cmd.exe /ru SYSTEM
  ```

- **Detection:** 50+ registry modification events (Rule 92307)
  - Latency: 8–10 seconds

---

**Overall:** 100% attack phase coverage, sub-30-second detection-to-containment across the chain.
