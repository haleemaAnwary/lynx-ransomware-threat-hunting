# Methodology and results

## Scenario
Based on the December 2025 DFIR Report account of Lynx ransomware, the lab simulated:
1. Initial access using valid RDP credentials.
2. Host and network share discovery.
3. Lateral movement and privileged-account persistence in Active Directory.
4. Data collection and an external upload.
5. Deletion of backup-related resources and execution of a non-encrypting substitute payload.

## Baseline investigation
Wazuh and Sysmon detected multiple host behaviors, including RDP logons, network-share enumeration, account changes and backup inhibition. The baseline investigation did **not** reliably detect the simulated external upload or the final substitute payload execution as distinct high-priority events.

## Enhancements
Custom Wazuh rules and Suricata signatures addressed those gaps. Wazuh Active Response logged matching events and terminated simulated processes through a PowerShell action. The final report records test evidence for rules 100113 and 100127, Suricata SID 1000001, and process termination.

## Interpretation
The results demonstrate detection tuning and response validation under **controlled lab conditions**. They do not establish coverage of all variants of the real Lynx malware, nor performance in production.

## Source
[The DFIR Report — Cat's Got Your Files: Lynx Ransomware](https://thedfirreport.com/2025/12/17/cats-got-your-files-lynx-ransomware/)
