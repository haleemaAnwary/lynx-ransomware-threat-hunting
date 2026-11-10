# Lynx Ransomware Threat Hunting & Automated Incident Response

**Academic security project | SPR600 | April 2026**

A hands-on threat hunting and detection engineering case study based on the [DFIR Report's Lynx ransomware investigation](https://thedfirreport.com/2025/12/17/cats-got-your-files-lynx-ransomware/). The project recreated a documented attack sequence in an isolated Windows Active Directory training environment, evaluated detection gaps, then implemented and tested additional monitoring and automated response.

**Project evidence:** [Full academic report (PDF)](docs/Lynx_project.pdf) · [Detection specifications](docs/detection-notes.md) · [Methodology and results](docs/methodology-and-results.md)

## Technologies
Wazuh SIEM · Sysmon · Windows Security Event Logs · Suricata IDS · Zeek · Active Directory · Windows Server · Ubuntu · VirtualBox · Vagrant · PowerShell · Bash · MITRE ATT&CK

## Lab and approach
The environment used the prebuilt **CapsuleCorp** Active Directory lab (credited to Royce Davis), including domain-joined Windows servers, a Wazuh manager, and network sensors. The simulation covered credential-based RDP access, discovery, lateral movement, privileged account changes, persistence, collection, exfiltration, backup inhibition, and simulated ransomware execution. **A substitute executable was used; actual Lynx ransomware was not deployed.**

1. Emulate the published attack behaviors in a controlled lab.
2. Investigate endpoint and network events in Wazuh and Suricata.
3. Identify gaps in the baseline detection coverage.
4. Implement custom detections and Wazuh Active Response.
5. Re-test the simulated behaviors and document observed results.

## Documented outcomes

| Area | Result |
|---|---|
| Privileged account abuse | Custom Wazuh rules 100101–100103 fired |
| Backup inhibition | Wazuh rules 100106–100107 fired |
| Collection / staging | Wazuh rules 100110–100111 fired |
| External file upload | Suricata SID 1000001 fired (SID 1000002 was authored; separate firing not shown) |
| Simulated ransomware execution | Rules 100113 and 100127 fired |
| Automated response | Wazuh response logging and PowerShell process termination verified in the lab |

These are selected lab-test results, not production detection accuracy measurements.

## Repository contents
- [Architecture](docs/architecture.md)
- [Detection notes](docs/detection-notes.md)
- [Methodology and results](docs/methodology-and-results.md)
- [Publication notes](docs/publication-notes.md)
- [Full project report (PDF)](docs/Lynx_project.pdf)

## Scope and limitations
This is an **academic case study**, not a ready-to-run reproduction. Original VM images, logs, and complete source files were not provided for this portfolio. Rule specifications are descriptive unless complete executable originals are added. The simulation used an inert substitute instead of actual ransomware. The uploaded report documents lab observations rather than a production deployment.

**Credits:** The original intrusion analysis is by The DFIR Report. CapsuleCorp is a third-party training environment. This portfolio describes work performed for the academic project.
