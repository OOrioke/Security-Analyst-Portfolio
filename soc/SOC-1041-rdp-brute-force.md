# SOC-1041: Multiple failed logons followed by success

**Track:** SOC Analyst  
**Level:** Beginner  
**Source:** Windows Security / Splunk ES  
**Date:** 2026-10-13 03:12 UTC

## Scenario
A burst of failed logons hit an internet-facing jump server, followed by a successful logon for the same account.

- **Host:** JMP-SRV-02
- **Account:** svc_backup
- **Source IP:** 185.220.101.47
- **Logon type:** 10 (RDP)

## My decisions
- **Verdict** True positive: malicious activity
- **Which ATT&CK technique best fits the initial access?** T1110.001 Brute Force: Password Guessing
- **Best next action** Disable svc_backup, isolate JMP-SRV-02, block the IP, and escalate to Tier 2

## My analysis
Several bursts of logon attempts were made from a remote IP address: 185.220.101.47 beginning at 03:10:02 with a successful logon at 03:12:09 on svc_backup after over 412 more events from the remote IP address. Believed to be a brute force attack.
svc_backup was disabled. JMP-SRV-02 was isolated. The IP address blocked and escalated to Tier 2

<details><summary>Questions this report answers</summary>

- What evidence shows the password guessing worked? Mention the number of failures and the success line.
- What did the attacker do right after logging in?
- Which containment steps did you choose, and why can't they wait?

</details>

## Detection (SPL)
```
index=wineventlog (EventCode=4625 OR EventCode=4624) host=JMP-SRV-02
| stats count(eval(EventCode=4625)) as failures
        count(eval(EventCode=4624)) as successes
        by src_ip, Account_Name
| where failures > 20 AND successes > 0
```

---
*Training scenario from my SOC Triage Range practice tool. All organizations, people, and data are fictional.*
