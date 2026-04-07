# Investigating-with-Splunk

## Objective
Investigate a compromised Windows environment using Splunk to identify a backdoor user account, malicious PowerShell execution, WMIC remote command execution, and C2 communication. The goal was to reconstruct the full attack chain from initial compromise to lateral movement.

### Skills Learned
- Advanced Splunk SPL queries for Windows log correlation
- Backdoor user account detection (Event ID 4720, 4732)
- Malicious PowerShell detection (Event ID 4103, 4104)
- WMIC remote execution analysis
- C2 communication identification and IOC extraction

### Tools Used
- Splunk SIEM (SPL)
- Windows Security Event Logs
- PowerShell Script Block Logging
- Sysmon
- MITRE ATT&CK framework

## Steps
The investigation began by searching for newly created user accounts (Event ID 4720) and group membership changes (Event ID 4732) to identify the backdoor account. PowerShell Script Block Logging was queried to extract the decoded malicious scripts. WMIC remote execution was identified through process creation logs showing wmic.exe with remote target arguments. Network connections from the compromised host were analyzed in Splunk to identify the C2 endpoint. Each finding was mapped to MITRE ATT&CK techniques (T1136, T1059.001, T1047, T1071).

*Ref 1: SPL query identifying backdoor account creation via Event ID 4720*
*Ref 2: PowerShell script block log showing decoded malicious command*
