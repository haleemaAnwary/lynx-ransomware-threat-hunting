# Detection and response notes

This document summarizes rules **reported as implemented** in the academic lab. These are **not executable configuration files** and should not be copied into production.

| Technique / phase | Documented detection |
|---|---|
| Account creation, privilege escalation | Wazuh 100101, 100102, 100103 |
| Scheduled backup task / VSS deletion | Wazuh 100106, 100107 |
| Collection and staging | Wazuh 100110, 100111 |
| Suspicious payload / command flags | Wazuh 100113 and 100127 (plus supporting rules) |
| HTTP traffic to temporary file sharing | Suricata SID 1000001 and SID 1000002 |

The report specifically shows **SID 1000001** firing. It does not independently prove that SID 1000002 fired.

## Automated response
The report describes two Wazuh Active Response actions for a high-confidence simulated ransomware execution alert:
- `lynx-response.sh` records a timestamped event in a server-side audit log.
- `kill_by_pid.ps1` processes an alert on the Windows agent and terminates the matched test process.

The original complete scripts are not included in this portfolio. The reported verification was a controlled test, not proof of safe operation in production.
