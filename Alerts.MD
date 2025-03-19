### Alert Name: A new Schedule task created
#### Description: Adversaries may create or modify Windows services to repeatedly execute malicious payloads as part of persistence. When Windows boots up, it starts programs or applications called services that perform background system functions.[1] Windows service configuration information, including the file path to the service's executable or recovery programs/commands, is stored in the Windows Registry.

Adversaries may install a new service or modify an existing service to execute at startup in order to persist on a system. Service configurations can be set or modified using system utilities (such as sc.exe), by directly modifying the Registry, or by interacting directly with the Windows API.
#### MITRE:  T1543


```bash
index="botsv1" source="WinEventLog:Microsoft-Windows-Sysmon/Operational" Image="C:\\Windows\\System32\\sc.exe"
| rex field=CommandLine "(?i)sc.exe\s+(?<action>\w+)\s+(?<service_name>\S+)"
| search action IN ("create", "config", "delete", "failure", "start", "stop", "pause", "continue")
| stats count by _time, action, service_name, Image, User, host
| where count > 0
| sort - _time
```

```bash
1️⃣ Resolve Status:
➡️ TP / FP / NTP (True Positive / False Positive / Non-Threat Positive)

2️⃣ Explanation:
➡️ Briefly describe why this alert was triggered and what was found during the investigation.

3️⃣ Comments:
➡️ Any additional insights, context, or related observations?

4️⃣ Actions Taken:
➡️ List the immediate steps taken to contain, remediate, or investigate the issue.

5️⃣ Recommended Actions:
➡️ Suggestions for future mitigation, tuning detections, or additional investigation.

6️⃣ Requires Escalation:
➡️ Y / N (If Yes, mention whom to escalate to & why.)
```


