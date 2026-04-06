# My Journey through cyber safety

A living portfolio and learning journal focused on the **SOC Analyst (Blue Team)** path.  
I document notes, writeups, detection logic, and templates as I work through rooms, courses, and home-lab exercises.

---

## 🎯 Focus

**SOC Analyst Tier 1 → Tier 2 progression**

- Monitoring and triaging security alerts
- Log analysis (Windows Event Logs, Sysmon, network traffic)
- SIEM (Splunk, Elastic/Kibana)
- Threat detection and incident response basics
- Understanding attacker TTPs (MITRE ATT&CK framework)

---

## 🛠️ Tools (building familiarity)

| Category | Tools |
|---|---|
| SIEM | Splunk, Elastic Stack |
| Network analysis | Wireshark, tcpdump |
| Endpoint telemetry | Sysmon, Windows Event Logs |
| Threat intelligence | VirusTotal, MISP (learning) |
| Detection engineering | Sigma rules, SPL queries |
| Practice platforms | TryHackMe, Blue Team Labs Online |

---

## 📁 Repo Structure

```
.
├── notes/
│   └── tryhackme/        # Room-by-room notes
├── Coursera/
│   └── Cisco-Cybersecurity-Operations-Fundamentals-Specialization/  # Cisco-provided courses on Coursera
├── TryHackMe/
│   └── SOC-Level-1/      # TryHackMe SOC Level 1 path overview + notes
├── templates/            # Reusable analyst workflow templates
├── cheatsheets/          # Quick-reference command/query sheets
├── detections/
│   ├── splunk/           # SPL detection queries
│   └── sigma/            # Sigma detection rules
└── glossary.md           # Core SOC terminology
```

---

## 📈 Progress Tracker

| Track | Platform | Status |
|---|---|---|
| SOC Fundamentals | TryHackMe | ✅ Completed (2026-04-06) |
| SOC Level 1 | TryHackMe | 🟡 Started (Path) |
| Cisco — Cybersecurity Operations Fundamentals Specialization | Coursera (Cisco) | 🟡 Started (Course 01: SOC) |

---

## 🎓 Coursera Journey (Cisco)

### Cisco — Cybersecurity Operations Fundamentals Specialization (on Coursera)
**Content provider:** Cisco  
**Learning platform:** Coursera  
**Status date:** 2026-04-06

#### Courses (in order)
- [ ] 01. Security Operations Center (SOC) — **In progress**
- [ ] 02. Endpoints and Systems
- [ ] 03. Network Security
- [ ] 04. Data Security
- [ ] 05. Threat Analysis
- [ ] 06. Threat Investigation
- [ ] 07. Threat Response

**Progress + notes:** `Coursera/Cisco-Cybersecurity-Operations-Fundamentals-Specialization/`

---

## 🧪 TryHackMe Journey (SOC)

### TryHackMe — SOC Level 1 (Path)
**Content provider:** TryHackMe  
**Learning platform:** TryHackMe  
**Status date:** 2026-04-06

#### Topics (in order)
- [ ] 01. Blue Team Introduction — **In progress**
- [ ] 02. SOC Team Internals
- [ ] 03. Core SOC Solutions
- [ ] 04. Cyber Defence Frameworks
- [ ] 05. Phishing Analysis
- [ ] 06. Network Traffic Analysis
- [ ] 07. Network Security Monitoring
- [ ] 08. Web Security Monitoring
- [ ] 09. Windows Security Monitoring
- [ ] 10. Linux Security Monitoring
- [ ] 11. Malware Concepts for SOC
- [ ] 12. Threat Analysis Tools
- [ ] 13. SIEM Triage for SOC
- [ ] 14. SOC Level 1 Capstone Challenges

**Progress + notes:** `TryHackMe/SOC-Level-1/`

---

## 📝 How I Write Up Rooms

Every room or module gets its own Markdown file following a consistent format.  
See the template for the structure I use: [`templates/alert-triage-template.md`](templates/alert-triage-template.md)

TryHackMe notes live in `notes/tryhackme/` — one file per room, named after the room slug (e.g., `soc-fundamentals.md`).

---

> **Note:** This repository contains only study notes, sanitized lab observations, and templates.  
> No real credentials, logs, flags, tokens, or sensitive data are included.
