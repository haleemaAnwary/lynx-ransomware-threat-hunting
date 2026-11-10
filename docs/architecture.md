# Lab architecture

- **Training domain:** CapsuleCorp Active Directory environment (prebuilt third-party lab)
- **Endpoints:** Windows Server domain controller and member servers
- **Telemetry:** Sysmon and Windows Security Event Logs forwarded by Wazuh agents
- **Monitoring:** Wazuh manager/dashboard on Ubuntu
- **Network sensors:** Suricata IDS and Zeek on a lab router
- **Attacker simulation:** Controlled Ubuntu host reproducing documented intrusion behaviors

The lab simulated several stages of the Lynx ransomware incident. The final phase used a substitute executable, not an actual encryption payload. See the academic report for the complete host inventory and experimental evidence.
