# Incident Report Template

> Use this template for any escalated or confirmed incident. Keep language factual and timeline-based.

---

## Incident Overview

| Field | Value |
|---|---|
| Incident ID | |
| Date / Time detected (UTC) | |
| Date / Time reported (UTC) | |
| Severity | Critical / High / Medium / Low |
| Status | Open / Contained / Resolved / Closed |
| Lead analyst | |

---

## Executive Summary

*One short paragraph: what happened, what was affected, and what was done.*

```
<!-- write summary here -->
```

---

## Detection

- **How was the incident detected?** (SIEM alert, user report, threat hunt, etc.)
- **Initial alert / ticket:** 
- **Detection rule / query:** 

---

## Timeline

All times in UTC.

| Timestamp (UTC) | Event |
|---|---|
| | Incident detected |
| | Analyst begins triage |
| | Escalated to Tier 2 |
| | Containment action taken |
| | Remediation complete |
| | Incident closed |

---

## Scope & Impact

| Field | Value |
|---|---|
| Systems affected | |
| Users affected | |
| Data potentially accessed | |
| Business impact | |

---

## Root Cause Analysis

*What allowed this incident to occur? Be specific about the initial access vector.*

```
<!-- write root cause here -->
```

---

## Containment Actions

- [ ] Isolated affected host(s)
- [ ] Disabled compromised account(s)
- [ ] Blocked malicious IP(s) / domain(s) at firewall/proxy
- [ ] <!-- add containment steps taken -->

---

## Eradication & Recovery

- [ ] Removed malicious artifacts
- [ ] Patched / hardened affected systems
- [ ] Reset credentials for affected accounts
- [ ] Verified clean state before reconnecting to network
- [ ] <!-- add steps -->

---

## Lessons Learned

| Question | Answer |
|---|---|
| What worked well? | |
| What could be improved? | |
| Detection gap identified? | |
| Recommended rule / alert improvement | |

---

## References

- <!-- link to relevant KB article, MITRE technique, or playbook -->
