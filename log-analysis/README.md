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

### Question 1: What bootstrap was installed?

The investigation began by locating the executable downloaded by the user's web browser. Process creation events were reviewed (uaing the word find feature for "http") to identify the bootstrap executable responsible for initiating the malware installation.

![VLAN Creation](screenshots/Bootstrapexe.png)

We can see the bootstrap was named "agentinstall.layer.io"

### Question 2: What's the name of the Main Agent Executable launched by the bootstrap?

By following the event log, we can demonstrate that the process "layer_agent_svc.exe" only runs after the bootstrap, meaning this was the executable.

![VLAN Creation](screenshots/LayerAgentSvc.png)

### Question 3: Which Powershell cmdlet is used to create the agent's Firewall Rules?

By using the word search feature ("Powershell"):

![VLAN Creation](screenshots/NewNetFireWall.png)

We can see the service "New-NetFireWallRule" with the display name "Layer Agent Service", linking them together.

### Question 4: Which program is executed to verify the Main Agent is running?

Scrolling the log, we can see task manager (Taskmgr.exe) being ran after the bootstrap, which would be a program capable for monitoring if the Main Agent was running.

![VLAN Creation](screenshots/Taskmgr.png)

### Question 5: What was the process ID of the executable used to re-enable Windows Defender?

Utilizing word seach ("Defender") Shows the process of Windows Defender as 1704.

![VLAN Creation](screenshots/ProcID.png)

This was enabled after the executable, fitting the timeline.

### Question 6: How many seconds after the last firewall rule was created was Defender Re-enabled?

To solve this, we need to find the Firewalls latest creation time, then subtract it from the Re-Enabled Microsoft Defender time.

![VLAN Creation](screenshots/Time1.png)

Last Firewall rule was recorded at 09:02:13.

![VLAN Creation](screenshots/Tim2.png)

Microsoft Defender was re-enabled at 09:02:59.

Therefore the time ellapsed was 46 seconds (59-13=46).

## Problem Set 2

### Question 1: What is the hostname?

Utilizing the search feature ("User") I was able to find the name of the host

![VLAN Creation](screenshots/ProcID.png)

>C:\Users\*john*\Desktop.







 ### Step 2 - Trace Process Execution

 Parent-child process relationships were examined to determine which executable launched after the initial bootstrap process. Following the execution chain provided insight into how the malware established itself on the system.

 ![VLAN Creation](screenshots/Bootstrapexe.png)

 ### Step 3 - Analyze System Modifications

 Powershell activity was reviewed to identify commands executed by the malware. Event logs revealed the creation of Windows Firewall rules. this indicates attempts to modify the host's security configurations.

 (SS)

 ## Takeaways
- Process creation logs provide valuable insight into malware execution
- Parent-child process relationships are essential for tracing attacker activity
- Powershell logs frequently reveal system configuration changes made by malware.

