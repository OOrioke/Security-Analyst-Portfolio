# SOC-1043: Account lockout after repeated failed logons

**Track:** SOC Analyst  
**Level:** Beginner  
**Source:** Active Directory  
**Date:** 2026-10-13 08:45 UTC

## Scenario
A user account was locked out after 25 failed logons. The help desk notes show the user changed their password yesterday.

- **Account:** m.chen
- **Source host:** HR-WS-044 (user's own desk PC)
- **Failure reason:** Bad password
- **Password last set:** 2026-10-12 16:02

## My decisions
- **Verdict** Benign true positive: real activity, but not an attack
- **Most likely cause** A mapped drive or saved credential still using the old password
- **Best next action** Have the user update the saved password for drive Z:, write notes, and close

## My analysis
Account m-chen failed logon after several attempts between 08:30:00 and 08:42:00 . Account locked at 08:42:00. Successful logon to user account at 08:44:10 at user workstation. User password was last changed 2026-10-12 16:02.

<details><summary>Questions this report answers</summary>

- Why did the account lock? Name the source computer, the logon type, and the 30-second timing.
- What told you this was not an attack?
- What fixed it, and what evidence would have changed your verdict?

</details>

## Detection (SPL)
```
index=wineventlog EventCode=4625 Account_Name=m.chen
| bin _time span=1m
| stats count by _time, Workstation_Name, Logon_Type
```

---
*Training scenario from my SOC Triage Range practice tool. All organizations, people, and data are fictional.*
