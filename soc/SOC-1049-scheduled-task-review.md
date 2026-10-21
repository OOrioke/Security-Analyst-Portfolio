# SOC-1049: New scheduled task created

**Track:** SOC Analyst  
**Level:** Beginner  
**Source:** Windows Security  
**Date:** 2026-10-13 09:15 UTC

## Scenario
A new scheduled task was registered on a workstation.

- **Host:** MKT-WS-063
- **Task:** \GoogleUpdateTaskMachineUA{4A1D…}
- **Created by:** SYSTEM
- **Binary:** C:\Program Files (x86)\Google\Update\GoogleUpdate.exe

## My decisions
- **Verdict** Benign true positive: legitimate software install
- **Which check most strongly supports your verdict?** A signed program in Program Files, matching an approved deployment seen on 212 hosts
- **Best next action** Close as expected, and suggest excluding signed tasks from approved deployments

## My analysis
System detected an event at 09:15:02. A new task was created which triggered the alarm. After reviewing it the alert was determined to be a legitimate software install.
Alert was checked to be certain it was not an attacker using it to stay on the machine.
The  file is digitally signed by Google LLC and did not show up in any antivirus as stated with SHA256.
Also the same task appeared on 212 other PCs that got the same deployment.
If the program lived in AppData or C:\Users\Public, was unsigned, or showed up on only one PC then it would be of concern and would be escalated.
Its been closed and suggesting that signed tasks be excluded from approved deployments.

<details><summary>Questions this report answers</summary>

- Why are new scheduled tasks worth checking at all?
- Which facts proved this one was legitimate?
- What would a malicious scheduled task have looked like?

</details>

## Detection (SPL)
```
index=wineventlog EventCode=4698
| rex field=Message "<Command>(?<task_cmd>[^<]+)"
| stats dc(host) as hosts values(host) as sample by TaskName, task_cmd
| sort hosts
```

---
*Training scenario from my SOC Triage Range practice tool. All organizations, people, and data are fictional.*
