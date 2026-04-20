SOC Incident Triage Report: [Room - SOC L1 Alert Triage]
Date: April 20, 2026
Analyst: Gladwin Joy
Status: Completed / Closed
________________________________________1. Summary
During this session, three distinct alerts were triaged within the TryHackMe SIEM environment. The alerts ranged from Critical to Low severity. Investigation revealed one True Positive (TP) involving social engineering/malicious file execution and two False Positives (FP)/Policy Queries related to standard business operations and developer activity.
2. Alert Triage Overview
Alert ID	Alert Name	Severity	Verdict	Flag Reference
001	Potential Data Exfiltration	Critical	False Positive	THM{looks_like_lots_of_zoom_meetings}
002	Double-Extension File Creation	High	True Positive	THM{how_could_this_user_fall_for_it?}
003	Download from GitHub Repo	Low	Benign / Policy	THM{should_we_allow_github_for_devs?}
________________________________________3. Detailed Investigation & Technical Analysis
Incident 001: Potential Data Exfiltration
●	Initial Trigger: High volume of outbound traffic detected from a single host.
●	Technical Analysis: Upon investigating the destination IPs and protocol, the traffic was mapped to known Zoom Video Communications infrastructure. The volume was consistent with high-definition video conferencing rather than unauthorized data tunneling.
●	Operational Context: The SIEM generated an alert due to an unusually large amount of data leaving the network. While this behavior mimics a data breach, analysis confirmed the user was simply participating in a high-bandwidth video conference.
●	Threat Mapping: MITRE ATT&CK T1048 - Exfiltration Over Alternative Protocol (Attempted Detection).
●	Remediation & Mitigation: Tuning the SIEM to baseline video conferencing traffic to prevent future "noisy" alerts.
Incident 002: Double-Extension File Creation
●	Initial Trigger: An endpoint detected a file created with a double extension (e.g., .pdf.exe).
●	Technical Analysis: This is a classic True Positive. Malicious actors use this to trick users into clicking what looks like a document but is actually an executable. The flag suggests a user was successfully phished.
●	Operational Context: An attacker bypassed user suspicion by disguising a malicious program as a standard PDF document. Because the operating system hides the true file type by default, the user believed they were opening a safe file, leading to a successful system compromise.
●	Vulnerability Context: While not a specific software CVE, this leverages CVE-1999-0504 (General design flaw in Windows that hides known file extensions by default).
●	Exploitation Vector: T1204.002 (User Execution: Malicious File). The user likely received the file via email (T1566 - Phishing).
●	Remediation & Mitigation: Isolate the affected host immediately, perform a full malware scan, and initiate a password reset for the compromised user. System Hardening Recommendation: Enforce a Group Policy Object (GPO) to globally display known file extensions to mitigate future masquerading attempts.
Incident 003: Download from GitHub Repository
●	Initial Trigger: Download of a ZIP archive/script from GitHub.com.
●	Technical Analysis: The activity was traced to a workstation assigned to the Development team. While GitHub is a common source for malware delivery (T1105 - Ingress Tool Transfer), the context here suggests authorized developer work.
●	Operational Context: The security system monitors code-sharing sites like GitHub because attackers frequently use them to host malware. In this instance, the download was traced to an authorized software developer performing standard duties, posing no threat to the network.
●	Verdict: Policy Inquiry. The organization needs to define if GitHub is a "sanctioned" site for all users or restricted to specific departments.
●	Remediation & Mitigation: Review organizational policy regarding sanctioned repositories and adjust SIEM alerting logic to suppress standard development subnets while alerting on restricted zones.
________________________________________4. Analyst Notes for Future Reference
Room Priority Strategy:
In this room, the priority was correctly identified:
●	Data Exfiltration (Critical) was handled first due to the potential for immediate massive data loss.
●	Double-Extension (High) followed, identifying a successful compromise.
●	GitHub (Low) was last, as it is often a routine operational event.
Key Takeaway: A "Critical" alert isn't always a "True Positive." The ability to distinguish between a Zoom meeting and an actual data breach is what separates a junior analyst from a senior one.
The Concept of "Tuning":
Notice how the remediation for the False Positives isn't just "ignore it next time." A major part of an L1 Analyst's job is making the SIEM smarter. If you get 50 alerts a day for Zoom meetings, you'll eventually miss the real alert hiding in the pile. "Tuning" means writing rules to tell the system, 'If traffic = Zoom AND volume = X, do not alert.'
Understanding Masquerading (Double Extensions):
This is one of the oldest but most effective tricks in cybersecurity.
●	A file named invoice.pdf is safe.
●	A file named invoice.exe is suspicious, and a user might not click it.
●	A file named invoice.pdf.exe looks exactly like invoice.pdf to the user because Windows hides the .exe at the very end.








SOC Incident Triage Report: [Room - SOC L1 Alert Reporting]
Date: April 20, 2026
Analyst: Gladwin Joy
Status: Completed / Escalated
________________________________________
1. Summary
During this session, alert reporting and escalation procedures were executed within the TryHackMe SIEM environment. The investigation prioritized a high-risk spearphishing campaign targeting IT management and a critical web shell deployment on a legacy Exchange server. Both alerts were thoroughly documented using the Five Ws framework and formally escalated to Level 2 (L2) analysis.
2. Alert Triage Overview
Alert ID	Alert Name	Severity	Verdict	Flag Reference
001	Microsoft Teams Phishing Attempt	High	True Positive	THM{nice_attempt_faking_microsoft_support}

THM{good_job_escalating_your_first_alert}
002	Web Shell via Old Exchange	Critical	True Positive	THM{looks_like_webshell_via_old_exchange}
________________________________________
3. Detailed Investigation & Technical Analysis
Incident 001: Microsoft Teams Phishing Attempt & Escalation
•	Initial Trigger: Post-delivery automated analysis flagged a suspicious email targeting a high-privileged user account.
•	Technical Analysis (The Five Ws):
o	Who: Eddie Huffman, IT Manager (e.huffman@tryhackme.thm).
o	What: Received an email with the subject "Important Update: Microsoft Teams Pricing Increase" containing a suspicious attachment named REPORT.rar.
o	When: March 27, 2025 at 19:25.
o	Where: Delivered to the user's corporate inbox.
o	Why/Weapon: Social engineering leveraging urgency ("600% price increase"). The sender domain (support@microsoft.com) was spoofed, confirmed by SPF and DKIM security check failures.
•	Operational Context: An attacker attempted to trick an IT Manager into opening a compressed file (.rar) by faking an urgent billing notice from Microsoft. We know it is fake because email security protocols (SPF/DKIM) act like digital signatures; both failed, proving the email did not originate from legitimate Microsoft servers.
•	Threat Mapping: MITRE ATT&CK T1566.001 (Phishing: Spearphishing Attachment), T1036.008 (Masquerading: Email Spoofing).
•	Remediation & Mitigation: * Purge the malicious email from the user's inbox and network mail queues.
o	Escalation Action: The alert context was fully documented and successfully escalated to L2 Analyst E. Fleming for advanced payload analysis of the .rar file.
Incident 002: Web Shell Execution via Legacy Exchange
•	Initial Trigger: SIEM alert indicating suspicious web server activity and unauthorized file creation on a Microsoft Exchange server.
•	Technical Analysis: The system detected characteristics of a web shell deployment. Web shells are malicious scripts uploaded to a compromised server, allowing remote attackers persistent, backdoor command-line access.
•	Operational Context: A threat actor exploited an unpatched vulnerability in an older version of Microsoft Exchange (the software that handles corporate email). By breaking in through this old software, they dropped a tool (a web shell) that lets them control the server through their web browser, essentially giving them the keys to the email server.
•	Vulnerability Context: This activity is highly indicative of well-known legacy Exchange exploits, commonly leveraging vulnerabilities such as ProxyShell (CVE-2021-34473) or ProxyLogon (CVE-2021-26855).
•	Exploitation Vector: MITRE ATT&CK T1505.003 (Server Software Component: Web Shell), T1190 (Exploit Public-Facing Application).
•	Remediation & Mitigation:
o	Immediate: Isolate the affected Exchange server from the internet and internal network to severe the attacker's connection.
o	Escalation Action: Escalated to L2/Incident Response team for memory forensics and to determine the scope of the breach.
o	System Hardening Recommendation: Apply all pending Microsoft Exchange security patches and mandate a migration of legacy on-premise servers to updated, supported infrastructure.
________________________________________
4. Analyst Notes for Future Reference
The Importance of the "Five Ws" in Escalation:
When escalating an alert to an L2 analyst (like E. Fleming), providing the Who, What, When, Where, and Why is mandatory. Raw SIEM logs are often only stored for 3 to 12 months to save space, but written alerts are kept indefinitely. A well-written summary becomes the permanent historical record of the attack.
Email Authentication (SPF/DKIM):
When investigating phishing, checking SPF (Sender Policy Framework) and DKIM (DomainKeys Identified Mail) is the fastest way to verify a sender. If an email claims to be from microsoft.com but SPF/DKIM fail, it definitively proves the sender is spoofing the domain from an unauthorized mail server.
Web Shells & Legacy Systems:
A web shell on a public-facing email server is a critical emergency. It means the perimeter defense has entirely failed. Attackers constantly scan the internet for "legacy" (old and unpatched) Exchange servers because the exploit codes (like ProxyShell) are public and easy to use. Keeping public-facing applications patched is the primary defense against this vector.

