**Windows Forensic 1** Jumping into the Windows Forensics 1 room was a pretty cool switch-up from my usual pen-testing tasks. Instead of breaking in, I was playing detective, digging through the Windows Registry using tools like EZTools and RegistryExplorer. It is fascinating how much of a footprint someone leaves behind—like figuring out exactly when a specific USB was plugged in or tracking down recently executed files through artifacts like AmCache and BAM/DAM. I ended up filling a few pages of my notebook by hand just mapping out the different hive paths like SAM, SECURITY, and SYSTEM so I wouldn't forget them during my next assessment. It really put into perspective how every offensive move I make leaves a trace, which is definitely going to change how I approach my next authorized security test. Overall, getting hands-on with the triage data and figuring out which user accounts were active, right down to extracting their password hints, made all those dry operating system concepts from theory learning trough coursera suddenly make perfect sense.

And i have made a small real life report based on the final hands on task of this room.

**Windows Registry Forensics Investigation Report**
Target System: Research Lab Desktop (Organization X)

**Investigator: Junior Forensic Analyst**

**Date of Investigation: June 1, 2026**

**1. Executive Summary**
An investigation was conducted on a desktop from the Organization X research lab suspected of unauthorized access. The objective was to analyze the extracted Windows Registry hives to identify user accounts, login history, file access, and external device connections.

The analysis confirmed that multiple user accounts exist on the system, a file named Changelog.txt was accessed, an installer was run from a mapped network drive, and an external USB storage device was attached.

**2. Evidence Processing**
The registry hives were loaded into RegistryExplorer. Because the hives were flagged as "dirty" due to uncommitted transaction logs, the .LOG1 and .LOG2 files were integrated to replay the transaction logs and create clean hives for analysis before proceeding.

**3. Forensic Findings**
As visible in the challenge dashboard from image_f0cbe0.png, the following details were successfully recovered from the registry hives:

User Account Discovery
By analyzing the SAM (Security Accounts Manager) hive, the account structures were mapped out to see who had access to this desktop:

Total User-Created Accounts: There are 3 user-created accounts present on the system.

Unused Account: The username thm-user2 was created but has never actually logged into the machine.

Account Security Hint: A user account named THM-4n6 was identified. The recovered password hint configured for this specific account is count.

Evidence of File and Program Execution
By looking at user execution artifacts (such as the NTUSER.dat hive and Recent Files keys), specific file interaction and execution paths were recovered:

File Access Tracking: The text file Changelog.txt was accessed on 2021-11-24 18:18:48.

Software Execution: A Python installation file was executed on the system. The complete path from where it ran is Z:\setups\python-3.8.2.exe. This confirms the system was connected to a network share or external drive mapped to the Z: letter.

External Hardware Connection
By analyzing the SYSTEM hive (specifically looking at the USBSTOR and Lifecycle keys), external media tracking was performed:

USB Connection Timestamp: A USB device with the friendly name 'USB' was found in the artifacts. Its last recorded connection time to the system was 2021-11-24 18:40:06.

**4. Conclusion & Next Steps**
The registry data proves that unauthorized activity likely took place around the afternoon/evening of November 24, 2021. The execution of software from a Z: drive confirms network mapping or a network-attached resource was active, and the presence of the USB device shows potential data vector risks.

It is recommended to next check the event logs for network share connections around that same timeframe to see where the Z: drive was pointing, and examine the THM-4n6 user profile folder for any modified or exfiltrated files.
