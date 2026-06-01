KQL Threat Hunting Playbook
> **300 production KQL queries for Microsoft Defender XDR — built from real MSSP experience across 4 simultaneous enterprise environments.**
![Platform](https://img.shields.io/badge/Platform-Microsoft%20Defender%20XDR-blue)
![Language](https://img.shields.io/badge/Language-KQL-orange)
![MITRE ATT&CK](https://img.shields.io/badge/Framework-MITRE%20ATT%26CK-red)
[![Queries](https://img.shields.io/badge/Queries-300-green)]()
---
About
This repository contains production-grade KQL threat hunting queries built and refined during 2+ years of MSSP detection engineering — triaging 300–350+ monthly incidents across 4 simultaneous enterprise client environments using Microsoft Defender XDR.
Every query here has a purpose. These are not copy-pasted from documentation. They were written to fill gaps in default alerting, reduce false positives, and hunt proactively before incidents become breaches.
---
Repository Structure
```
├── identity/                    # Sign-in anomalies, privileged accounts, MFA gaps
├── cloud-apps/                  # CloudAppEvents — SaaS risky activities, OAuth abuse
├── email-phishing/              # Email, URL clicks, phishing campaigns (multi-table)
├── endpoint/                    # Process, network, registry, file system
├── lateral-movement/            # RDP, SMB, PsExec, remote admin tools
├── ai-agents/                   # AIAgentsInfo — Copilot Studio & AI agent security
├── multi-signal/                # Cross-table kill chain correlations
└── baseline/                    # Reusable baseline building blocks
```
---
Query Coverage — 300 Queries Across 35 Sections
Section	Coverage	Queries
Identity Sign-In Anomalies	High-risk sign-ins, new countries, unmanaged devices	4
Legacy Auth & MFA	Single-factor, legacy protocols, CA bypass	3
Privileged Account Monitoring	Admin risky sign-ins, break-glass accounts	3
Impossible Travel	Haversine formula, risky IP clustering	2
Password Spray & Brute Force	Spray detection, brute force, success-after-failure	3
Cloud App Risky Activities	UEBA baseline, mass downloads, anonymous proxy	4
Cloud Storage Exfiltration	Failed ops, anonymous access, suspicious user agents	3
OAuth & Graph API Abuse	High-privilege OAuth, risky apps, SPN Graph activity	3
Email & Phishing	Malware delivery, ZAP, URL clicks, campaign clustering	4
Teams & Collaboration	Teams malware, post-delivery remediation, malicious URLs	3
Endpoint Process Anomalies	New processes, LOLBins, Office macro spawns	3
Endpoint Network & C2	Rare ports, DNS tunneling, container outbound	3
Malware & Malicious Content	AV by family, FileMaliciousContentInfo	2
Persistence & Autoruns	Run keys, shell extensions	2
Lateral Movement	RDP, SMB, PsExec	3
Domain Controller & Directory	Privileged group changes, password resets	2
UEBA Behaviors	High-risk behaviors, multi-behavior users, entity linking	3
AI Agents & Exposure Graph	AIAgentsInfo — Copilot Studio security, attack paths	9
Identity & SPN Sign-ins	SPN failures, managed identity geo anomalies, CA failure	5
Identity Inventory & Risk	Criticality + risk, stale accounts, high-role-count	4
Cloud Apps — SaaS Activity	OS anomaly, impersonation, first-time apps	5
Cloud Control Plane	Resource creation/deletion, bulk API from single IP	4
Cloud Workload Processes	New container images, shell in containers	3
Cloud DNS	New domain baseline, NXDOMAIN spike, DGA heuristic	5
Cloud Storage Patterns	Tor access, suspicious IPs, anonymous from private ranges	4
Email & URL Variants	QR phishing, frequent malicious clickers, URL chains	4
Teams Messaging	External threads with malware, malicious domain clustering	2
Graph API Abuse	Role escalation via Graph, new IPs on Graph	2
Exposure Graph Extended	Internet→critical edges, internal+exposed nodes	4
Endpoint File System & DLL	Startup persistence, temp drops, DLL sideloading	10
Teams Post-Delivery	ZAP, manual remediation, external thread cleanup	4
DeviceInfo Enrichment	Internet-facing high-exposure, poor sensor health	5

Multi-Signal Correlations	Risky sign-in → cloud anomaly → AV kill chain	20
Baseline Building Blocks	Countries, apps, devices, ports, behavior baselines	12
Misc Advanced Joins	Cross-table anomaly seeds, AI agent risk scenarios	20
---
How to Use
Ad-hoc hunting:
Open Microsoft Defender XDR → Advanced Hunting
Copy any `.kql` file content
Adjust tunable parameters (lookback window, thresholds)
Run
Continuous monitoring:
Save as a Custom Detection Rule. Recommended frequencies:
High-severity (spray, brute force, exfil): 1-hour
Medium hunting queries: Daily
Baseline builders: Weekly
Microsoft Sentinel:
Replace `Timestamp` with `TimeGenerated` throughout. Most tables (`CloudAppEvents`, `EntraIdSignInEvents`, `IdentityLogonEvents`) are available natively in Sentinel workspaces.
---
AI Security Extension
For AI-native threat detections (XPIA, Copilot abuse, AI agent security), see the companion repository:
sagarm365/ai-threat-detection
That repository contains detection rules specifically for:
Cross-Prompt Injection Attacks (XPIA) via M365 Copilot
AI agent excessive permission hunting
MITRE ATLAS mapped detections
---
Author
Sagar Patel — Detection Engineer | AI Security
SC-200 Microsoft Security Operations Analyst
MS-500 Microsoft 365 Security Administrator
SC-401 Microsoft Information Security Administrator
SentinelOne Incident Responder
2+ years MSSP detection engineering (4 simultaneous enterprise environments)
Published at detections.ai
Connect: LinkedIn | AI Threat Detection Repo
---
License
MIT — Use freely, credit appreciated.
---
If this repository helped you find something real in your environment, drop a ⭐
