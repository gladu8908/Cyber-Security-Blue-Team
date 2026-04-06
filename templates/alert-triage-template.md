# Alert Triage Template

> Copy this file for each alert you investigate. Fill in every section before closing or escalating.

---

## Alert Summary

| Field | Value |
|---|---|
| Date / Time (UTC) | |
| Alert ID / Ticket # | |
| SIEM rule / detection name | |
| Severity (P1–P4) | |
| Analyst | |

---

## Impacted Asset & User

| Field | Value |
|---|---|
| Hostname | |
| IP address | |
| Username | |
| Department / Business unit | |
| Asset criticality | |

---

## Event Timeline

List events in chronological order (timestamps in UTC):

| Timestamp (UTC) | Event | Source log |
|---|---|---|
| | | |
| | | |
| | | |

---

## Evidence

Paste sanitised log snippets, query results, or describe what you found:

```
<!-- paste sanitised log lines or query output here -->
```

---

## IOC List (Lab / CTF Only)

> Only record IOCs from lab or CTF environments — never from real incidents without authorisation.

| Type | Value | Context |
|---|---|---|
| IP address | | |
| Domain | | |
| File hash (MD5/SHA256) | | |
| File name | | |

---

## Hypothesis

What do you think happened and why?

```
<!-- write your hypothesis here -->
```

---

## Investigation Steps Taken

- [ ] Checked asset ownership and criticality
- [ ] Reviewed surrounding events (±15 min context window)
- [ ] Looked up IP/domain in threat intelligence
- [ ] Checked for similar alerts (same user / host / rule)
- [ ] <!-- add steps as you take them -->

---

## Verdict

- [ ] **False Positive** – reason: 
- [ ] **Benign True Positive** – expected behaviour, no action needed
- [ ] **Malicious True Positive** – escalate to Tier 2

---

## Next Actions / Close Notes

```
<!-- what was done, what ticket was created, what was escalated -->
```
