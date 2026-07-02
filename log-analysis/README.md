# Log Analysis

## Objective

Investigate system logs to reconstruct attacker activity, identify malicious processes, and determine how malware established persistence and modified the host environment.

## Skills Demonstrated
- Windows event log analysis
- Process tree investigation
- PowerShell analysis
- Timeline reconstruction
- Threat hunting
- Incident response

## Tools
- Windows Event Logs
- Sysmon Logs
- Log Viewer / Search Function

## Methodology 

## Problem 1

### Question 1: What boostrap was installed?

The investigation began by locating the executable downloaded by the user's web browser. Process creation events were reviewed to identify the bootstrap executable responsible for initiating the malware installation.

![VLAN Creation](../screenshots/Bootstrapexe.png)

 ### Step 2 - Trace Process Execution

 Parent-child process relationships were examined to determine which executable launched after the initial bootstrap process. Following the execution chain provided insight into how the malware established itself on the system.

 (SS)

 ### Step 3 - Analyze System Modifications

 Powershell activity was reviewed to identify commands executed by the malware. Event logs revealed the creation of Windows Firewall rules. this indicates attempts to modify the host's security configurations.

 (SS)

 ## Takeaways
- Process creation logs provide valuable insight into malware execution
- Parent-child process relationships are essential for tracing attacker activity
- Powershell logs frequently reveal system configuration changes made by malware.

