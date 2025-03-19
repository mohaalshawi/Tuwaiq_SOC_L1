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

```bash
index="botsv1" source="WinEventLog:Microsoft-Windows-Sysmon/Operational" Image="C:\\Windows\\System32\\sc.exe"
| rex field=CommandLine "(?i)sc.exe\s+(?<action>\w+)\s+(?<service_name>\S+)"
| search action IN ("create", "config", "delete", "failure", "start", "stop", "pause", "continue")
| stats count by _time, action, service_name, Image, User, host
| where count > 0
| sort - _time
```
