# SOC-1044: Impossible travel sign-in

**Track:** SOC Analyst  
**Level:** Intermediate  
**Source:** Entra ID sign-in logs  
**Date:** 2026-10-13 16:05 UTC

## Scenario
The same account signed in from Los Angeles and then Amsterdam 18 minutes apart.

- **User:** r.okafor
- **Sign-in 1:** Los Angeles, US — 104.28.x.x
- **Sign-in 2:** Amsterdam, NL — 193.33.112.10
- **MFA:** Passed on both

## My decisions
- **Verdict** Benign: explained by the corporate VPN
- **What evidence settles it?** The second IP is the company's own VPN server, and the laptop matches
- **Best next action** Close as benign and ask for the VPN addresses to be added to the rule's trusted locations

## My analysis
Alert was triggered at 16:05:40 for SignIn for user r.okafor from IP address 193.33.112.10. Alert triggered due to the location of sign in. There was a prior sign in at 15:47:12 from user r.okafor from ip 104.28.17.90 in Los Angeles. IP 193.33.112.10 is reporting Amsterdam as location. The distance of travel is greater than the sign in time between both location. After reviewing it was determined that IP address 193.33.112.10 belongs to the company's VPN server. It was closed as as benign and recommending for the VPN addresses to be added to the rule's trusted locations.

<details><summary>Questions this report answers</summary>

- Why did the impossible travel alert fire?
- What evidence cleared it, and why isn't MFA enough on its own?
- What rule change did you recommend?

</details>

## Detection (SPL)
```
index=azure sourcetype=azure:aad:signin user=r.okafor
| iplocation src_ip
| sort 0 _time
| table _time src_ip City Country deviceId
```

---
*Training scenario from my SOC Triage Range practice tool. All organizations, people, and data are fictional.*
