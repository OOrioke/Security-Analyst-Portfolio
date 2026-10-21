# TPRM-203: CareSched: online appointment booking

**Track:** Third-Party Risk (TPRM)  
**Level:** Beginner  
**Source:** Vendor security review  
**Date:** Review opened 2026-10-16

## Scenario
Outpatient clinics want an app that lets patients book appointments online. The vendor sent a SOC 2 report and a completed questionnaire.

- **Vendor:** CareSched (fictional)
- **Service:** Online patient appointment booking
- **Data shared:** PHI: names, birth dates, phone numbers, visit reasons
- **System access:** Connects to the EHR scheduling module
- **BAA:** Signed

## My decisions
- **What is the main limitation of the evidence?** It's a Type I report: controls were checked on one day, not tested over time
- **With PHI and an EHR connection, what tier is this vendor?** High
- **Best next action** Approve with conditions: require the Type II report by Feb 2027, track it, and reassess when it arrives

## My analysis
Finding: Only SOC 2 Type I available (design only, not tested over time)
Inherent risk: High (PHI + EHR connection) | Residual risk: Medium
Required action: Provide SOC 2 Type II report
Due: 2027-02-28
Owner: Vendor; tracked by TPRM
Decision: Approved with conditions

SOC 2 Type I reports provided by vendor. SOC 2 Type I only tests if controls are well designed on a single day compared to Type II which which tests control  over a period of time typically 6 to 12 months. Type II shows controls were followed.
The controls are good but not tested over the period of time of 6 to 12 months.
The is a "High" tier vendor being PHI will be accessed. 
vendor is to be approved with conditions which would be providing SOC 2 Type II by 2027-02-28 as forementioned by the vendor. 
Failure to provide SOC 2 Type II by 2027-02-28 should result in vendor's loss of access.

<details><summary>Questions this report answers</summary>

- Explain SOC 2 Type I vs. Type II in your own words.
- Why is conditional approval reasonable for this vendor?
- What deadline did you set, and what happens if they miss it?

</details>

## Risk finding
```
Finding: Only SOC 2 Type I available (design only, not tested over time)
Inherent risk: High (PHI + EHR connection) | Residual risk: Medium
Required action: Provide SOC 2 Type II report
Due: 2027-02-28
Owner: Vendor; tracked by TPRM
Decision: Approved with conditions
```

---
*Training scenario from my SOC Triage Range practice tool. All organizations, people, and data are fictional.*
