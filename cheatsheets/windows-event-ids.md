# Windows Event IDs – Quick Reference

> Starter cheat sheet. Add new IDs and notes as you encounter them in labs.

---

## Authentication & Account Events

| Event ID | Source | Description |
|---|---|---|
| 4624 | Security | Successful logon |
| 4625 | Security | Failed logon |
| 4634 | Security | Account logoff |
| 4648 | Security | Logon with explicit credentials (e.g., `runas`) |
| 4672 | Security | Special privileges assigned to new logon (admin rights) |
| 4720 | Security | User account created |
| 4726 | Security | User account deleted |
| 4740 | Security | User account locked out |

---

## Privilege & Group Changes

| Event ID | Source | Description |
|---|---|---|
| 4728 | Security | Member added to a security-enabled global group |
| 4732 | Security | Member added to a security-enabled local group |
| 4756 | Security | Member added to a security-enabled universal group |
| 4776 | Security | Domain controller attempted to validate credentials (NTLM) |

---

## Process & Execution Events

| Event ID | Source | Description |
|---|---|---|
| 4688 | Security | New process created (requires audit policy enabled) |
| 4689 | Security | Process terminated |

> **Tip:** Use Sysmon Event ID 1 (Process Creation) for richer process telemetry than 4688.

---

## Object Access & File Activity

| Event ID | Source | Description |
|---|---|---|
| 4663 | Security | Object access attempt (file/folder — requires SACL) |
| 4656 | Security | Handle to object requested |

---

## Windows Defender / Security Software

| Event ID | Source | Description |
|---|---|---|
| 1116 | Microsoft-Windows-Windows Defender/Operational | Malware detected |
| 1117 | Microsoft-Windows-Windows Defender/Operational | Action taken on malware |

---

## PowerShell / Script Logging

| Event ID | Source | Description |
|---|---|---|
| 4103 | Microsoft-Windows-PowerShell/Operational | Module logging (pipeline output) |
| 4104 | Microsoft-Windows-PowerShell/Operational | Script block logging (full script content) |

---

## Sysmon Reference (common IDs)

| Sysmon Event ID | Description |
|---|---|
| 1 | Process creation |
| 3 | Network connection |
| 7 | Image (DLL) loaded |
| 8 | CreateRemoteThread (injection indicator) |
| 11 | File created |
| 13 | Registry value set |
| 22 | DNS query |

---

> **Expand this file** as you encounter new event IDs in labs and rooms.  
> Always note the **log source** (Security, System, Application, Sysmon, PowerShell) alongside the ID.
