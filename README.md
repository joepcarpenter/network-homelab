[README.md](https://github.com/user-attachments/files/26523466/README.md)
# Bench Notes — J. Carpenter

> *Secure, Order, and things I take apart.*

CompTIA Network+ · Security+ · A+ · BTL1 (in progress) · AWS Cloud Practitioner (in progress)

Cumberland, MD · joe@jpcarpenter.com · [jpcarpenter.com](https://jpcarpenter.com)

---

## About This Repository

This repository documents hands-on security and infrastructure work built alongside formal certifications. Labs cover the full blue team stack — phishing analysis, threat intelligence, digital forensics, SIEM investigation, and incident response — plus the networking foundation underneath all of it.

Every lab has a writeup covering what was done, what was found, and what it proved. No walkthroughs copied from tutorials. No AI fabrications.

If you're a recruiter or hiring manager: the writeups are in the `labs/` directory. Please, start there.

---

## Lab Index

### 🔬 Phishing Analysis

| Lab | Status | What it demonstrates |
|-----|--------|----------------------|
| [Lab PA-01 — Email Header Forensics](labs/phishing/PA-01-email-header-forensics.md) | ✅ Complete | SPF/DKIM/DMARC analysis, relay tracing, originating IP identification |
| [Lab PA-02 — URL & Domain Investigation](labs/phishing/PA-02-url-domain-investigation.md) | ✅ Complete | IOC extraction, VirusTotal/URLScan analysis, RDAP lookup, threat reporting |
| [Lab PA-03 — Phishing Kit Analysis](labs/phishing/PA-03-phishing-kit-analysis.md) | 🔄 In Progress | HTML source analysis, credential harvesting identification, attacker infrastructure mapping |

### 🧠 Threat Intelligence

| Lab | Status | What it demonstrates |
|-----|--------|----------------------|
| [Lab TI-01 — IOC Enrichment](labs/threat-intel/TI-01-ioc-enrichment.md) | 📋 Planned | Multi-source IOC enrichment, threat actor attribution, campaign context |
| [Lab TI-02 — MITRE ATT&CK Mapping](labs/threat-intel/TI-02-mitre-attack-mapping.md) | 📋 Planned | Attack lifecycle mapping, TTP identification, kill chain analysis |
| [Lab TI-03 — Threat Actor Profile](labs/threat-intel/TI-03-threat-actor-profile.md) | 📋 Planned | OSINT research, historical campaign analysis, ATT&CK framework application |

### 🔍 Digital Forensics

| Lab | Status | What it demonstrates |
|-----|--------|----------------------|
| [Lab DF-01 — Windows Artifact Analysis](labs/forensics/DF-01-windows-artifacts.md) | 📋 Planned | Event log analysis, prefetch files, browser history, USB artifacts, timeline construction |
| [Lab DF-02 — Memory Analysis](labs/forensics/DF-02-memory-analysis.md) | 📋 Planned | Volatility, process analysis, network connections, injected code detection |
| [Lab DF-03 — File Metadata & Hash Analysis](labs/forensics/DF-03-file-metadata-hashes.md) | 📋 Planned | ExifTool, hash verification, file type mismatch detection, VirusTotal |

### 📊 SIEM & Log Analysis

| Lab | Status | What it demonstrates |
|-----|--------|----------------------|
| [Lab SI-01 — Splunk Log Investigation](labs/siem/SI-01-splunk-log-investigation.md) | 📋 Planned | SPL queries, Windows event log analysis, privilege escalation detection |
| [Lab SI-02 — Brute Force Detection](labs/siem/SI-02-brute-force-detection.md) | 📋 Planned | Authentication log analysis, pattern detection, alert rule development |
| [Lab SI-03 — Alert Triage](labs/siem/SI-03-alert-triage.md) | 📋 Planned | True/false positive classification, investigation documentation, escalation decisions |

### 🚨 Incident Response

| Lab | Status | What it demonstrates |
|-----|--------|----------------------|
| [Lab IR-01 — Incident Timeline Construction](labs/incident-response/IR-01-incident-timeline.md) | 📋 Planned | Log correlation, attacker action reconstruction, ATT&CK kill chain mapping |
| [Lab IR-02 — Containment & Eradication Playbook](labs/incident-response/IR-02-containment-playbook.md) | 📋 Planned | IR playbook development, NIST SP 800-61 methodology, ransomware response |
| [Lab IR-03 — Post-Incident Report](labs/incident-response/IR-03-post-incident-report.md) | 📋 Planned | Executive summary writing, technical timeline, root cause analysis, recommendations |

---

### 🌐 Network Infrastructure

| Lab | Status | What it demonstrates |
|-----|--------|----------------------|
| [Lab NI-01 — Small Business LAN Deployment](labs/networking/NI-01-lan-deployment.md) | ✅ Complete | Cisco IOS CLI, IP addressing, routing validation, documentation |
| [Lab NI-02 — VLAN Segmentation (Router on a Stick)](labs/networking/NI-02-vlan-segmentation.md) | ✅ Complete | 802.1Q trunking, inter-VLAN routing, TTL analysis, packet capture |
| [Lab NI-03 — Wireshark Traffic Analysis](labs/networking/NI-03-wireshark-analysis.md) | 🔄 In Progress | Live capture, ARP/ICMP/UDP analysis, traceroute investigation |
| [Lab NI-04 — FreePBX VoIP Deployment](labs/networking/NI-04-freepbx-voip.md) | 🔄 In Progress | Linux server deployment, SIP configuration, hosted voice simulation |
| [Lab NI-05 — Active Directory Environment](labs/networking/NI-05-active-directory.md) | 🔄 In Progress | Windows Server 2022, domain controller, OUs, GPO, workstation domain join |

---

## Tools & Environment

| Category | Tools |
|----------|-------|
| Analysis | Wireshark · Nmap · Autopsy · Volatility · ExifTool |
| Threat Intel | VirusTotal · URLScan.io · AbuseIPDB · Shodan · MITRE ATT&CK |
| SIEM | Splunk |
| Network | Cisco Packet Tracer · VirtualBox · Tailscale/WireGuard |
| OS | Pop!_OS Linux (daily driver) · Windows Server 2022 · Windows 10 |
| Development | VS Codium · Git · GitHub |

---

## Certifications

| Cert | Issuer | Status |
|------|--------|--------|
| CompTIA Network+ | CompTIA | ✅ 2026 |
| CompTIA Security+ | CompTIA | ✅ 2026 |
| CompTIA A+ | CompTIA | ✅ 2025 |
| CSIS — Secure Infrastructure Specialist | CompTIA | ✅ 2026 |
| CIOS — IT Operations Specialist | CompTIA | ✅ 2026 |
| BTL1 — Blue Team Level 1 | Security Blue Team | 🔄 In Progress |
| AWS Cloud Practitioner | Amazon | 🔄 In Progress |

---

*This repository is a living document. Labs are added as completed.*
*Last updated: April 2026*
