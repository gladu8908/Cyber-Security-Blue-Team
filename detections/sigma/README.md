# Sigma Detection Rules

This folder contains [Sigma](https://github.com/SigmaHQ/sigma) detection rules.  
Sigma is a vendor-agnostic, open-standard format for writing detection rules that can be converted to SPL, KQL, Lucene, and more.

---

## What is Sigma?

Sigma rules are written in YAML and describe suspicious log patterns in a backend-independent way.  
Use `sigma-cli` (or `sigmac`) to convert them to your target SIEM query language.

```bash
# Example: convert to Splunk SPL
sigma convert -t splunk -p splunk_windows my-rule.yml
```

---

## File Format

Each file in this folder is a `.yml` Sigma rule file. The standard header looks like this:

```yaml
title: Example Detection
status: experimental
description: Detects an example suspicious behaviour
author: your-name
date: YYYY/MM/DD
logsource:
    category: process_creation
    product: windows
detection:
    selection:
        CommandLine|contains: 'suspicious_string'
    condition: selection
level: medium
tags:
    - attack.execution
    - attack.t1059
```

---

## Resources

- [Sigma Rules GitHub](https://github.com/SigmaHQ/sigma)
- [sigma-cli](https://github.com/SigmaHQ/sigma-cli)
- [MITRE ATT&CK](https://attack.mitre.org/)

---

*Add your Sigma rule `.yml` files here as you write them.*
