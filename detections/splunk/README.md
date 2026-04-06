# Splunk SPL Detection Queries

This folder contains Splunk Search Processing Language (SPL) queries for detecting suspicious activity.  
Each query is written and tested in a lab or home-lab environment.

---

## File Format

Each detection is stored as a Markdown file (`.md`) with:
- A description of what the query detects
- The SPL query in a code block
- Notes on tuning and reducing false positives
- MITRE ATT&CK technique reference (where applicable)

---

## Example Query Structure

```markdown
## Detection: [Name]

**Description:** What the query detects  
**MITRE ATT&CK:** [Txxxx – Technique Name](https://attack.mitre.org/techniques/Txxxx/)  
**Data source:** Windows Security / Sysmon / etc.

### SPL Query

\`\`\`spl
index=* EventCode=4625
| stats count by src_ip, user, host
| where count > 5
\`\`\`

### Tuning Notes
- Exclude known service accounts
- Adjust threshold as needed for environment
```

---

## Queries

*Add your SPL query files here as you build them.*
