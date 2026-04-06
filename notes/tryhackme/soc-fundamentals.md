# SOC Fundamentals – TryHackMe

**Platform:** TryHackMe  
**Status:** 🟡 In Progress  
**Date started:** <!-- add date -->

---

## Objectives

- Understand what a Security Operations Centre (SOC) is and what it does.
- Learn the roles within a SOC team (Tier 1, Tier 2, Tier 3, SOC Manager).
- Understand the tools and data sources a SOC works with.
- Learn the basic alert triage and escalation process.

---

## Key Concepts

### What is a SOC?
A SOC is a centralised team (or function) responsible for continuously monitoring, detecting, analysing, and responding to cybersecurity events across an organisation.

### SOC Tiers

| Tier | Role | Primary task |
|---|---|---|
| Tier 1 | Alert Analyst | Monitor dashboards, triage incoming alerts, escalate |
| Tier 2 | Incident Responder | Deeper investigation of escalated alerts |
| Tier 3 | Threat Hunter / SME | Proactive hunting, advanced investigation |
| SOC Manager | Management | Process, metrics, communication with leadership |

### Key tools a SOC uses

- **SIEM** – aggregates and correlates logs (e.g., Splunk, Microsoft Sentinel, Elastic)
- **EDR** – endpoint detection and response (e.g., CrowdStrike, SentinelOne)
- **IDS/IPS** – network intrusion detection/prevention (e.g., Snort, Suricata)
- **Threat intelligence feeds** – known bad IPs, domains, hashes
- **Ticketing system** – tracks cases (e.g., TheHive, ServiceNow)

### Important terms

| Term | Meaning |
|---|---|
| IOC | Indicator of Compromise – artifact that suggests a breach (IP, hash, domain) |
| TTP | Tactics, Techniques, and Procedures – attacker behaviour patterns |
| False positive | Alert fired but no real threat exists |
| True positive | Alert fired and a real threat exists |
| MITRE ATT&CK | Framework mapping real-world attacker TTPs |

---

## SOC Workflow

```
Log/event generated
       ↓
SIEM ingests and correlates
       ↓
Alert fired → Tier 1 analyst reviews
       ↓
Triage: Is this a true positive?
  ├─ No  → Close / tune the rule
  └─ Yes → Escalate to Tier 2
               ↓
         Investigate → Scope impact
               ↓
         Contain / Remediate
               ↓
         Document and close case
```

---

## Questions / Things to Research Further

- [ ] What is the difference between an IDS and an IPS in practice?
- [ ] How does a SIEM correlation rule actually work? (explore SPL / KQL)
- [ ] What logs does Windows generate by default vs. with Sysmon?
- [ ] <!-- add your own questions as you work through the room -->
