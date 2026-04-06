# Detections

This folder contains detection logic written or adapted during labs and study.

> **Important:** All detection rules here are written for educational and home-lab purposes only.  
> Do not deploy untested rules to production environments without review and tuning.

---

## Folder Structure

```
detections/
├── splunk/     # Splunk SPL search queries and correlation rules
└── sigma/      # Sigma detection rules (vendor-agnostic YAML format)
```

---

## How to Use

| Folder | Format | How to run |
|---|---|---|
| `splunk/` | `.spl` or `.md` files with SPL queries | Paste into Splunk Search bar |
| `sigma/` | `.yml` Sigma rule files | Convert with `sigma-cli` to target backend |

---

## Naming Convention

Files are named descriptively using kebab-case:

```
splunk/detect-brute-force-login.spl
sigma/detect-lateral-movement-psexec.yml
```

---

## Credits & References

Where a rule is adapted from an existing public source, credit is included in the file header.
