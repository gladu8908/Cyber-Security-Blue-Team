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
├── templates/            # Reusable analyst workflow templates
├── cheatsheets/          # Quick-reference command/query sheets
├── detections/
│   ├── splunk/           # SPL detection queries
│   └── sigma/            # Sigma detection rules
└── glossary.md           # Core SOC terminology
```

---

## 📈 Progress Tracker

| Topic / Room | Platform | Status |
|---|---|---|
| SOC Fundamentals | TryHackMe | 🟡 Started |
| Windows Event Logs | TryHackMe | ⬜ Upcoming |
| Wireshark Basics | TryHackMe | ⬜ Upcoming |
| Splunk / SIEM Basics | TryHackMe | ⬜ Upcoming |
| Incident Response Process | Self-study | ⬜ Upcoming |

---

## 📝 How I Write Up Rooms

Every room or module gets its own Markdown file following a consistent format.  
See the template for the structure I use: [`templates/alert-triage-template.md`](templates/alert-triage-template.md)

Notes live in `notes/tryhackme/` — one file per room, named after the room slug (e.g., `soc-fundamentals.md`).

---

> **Note:** This repository contains only study notes, sanitized lab observations, and templates.  
> No real credentials, logs, flags, tokens, or sensitive data are included.
