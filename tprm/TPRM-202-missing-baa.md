# TPRM-202: MedScribe: radiology dictation transcription

**Track:** Third-Party Risk (TPRM)  
**Level:** Beginner  
**Source:** Vendor security review  
**Date:** Review opened 2026-10-16

## Scenario
Radiology wants a vendor to transcribe doctors' dictated reports. The contract is ready, and the business owner wants approval by Friday.

- **Vendor:** MedScribe Transcription (fictional)
- **Service:** Transcribe radiology dictations
- **Data shared:** PHI: names, record numbers, diagnoses
- **System access:** Upload portal; read access to dictation system
- **BAA status:** Not on file

## My decisions
- **What is the main gap?** No Business Associate Agreement (BAA) has been signed
- **Why does that gap matter?** HIPAA requires a BAA before a vendor receives PHI on the hospital's behalf
- **Best next action** Approve on one condition: no PHI is shared until the BAA is signed. Tell the business owner and Legal.

## My analysis
Finding: No Business Associate Agreement on file
Risk: High. Sharing PHI without a BAA violates HIPAA.
Required action: Sign BAA before any PHI is shared
Owner: Legal / Vendor Management
Due: Before go-live
Security review: Passed (SOC 2 Type II, no exceptions)
Decision: Approved with conditions

<details><summary>Questions this report answers</summary>

- What was strong about the vendor's security?
- What was missing, and what does HIPAA require before PHI is shared?
- How would you explain the decision to the business owner who wants to start Monday?

</details>

## Risk finding
```
Finding: No Business Associate Agreement on file
Risk: High. Sharing PHI without a BAA violates HIPAA.
Required action: Sign BAA before any PHI is shared
Owner: Legal / Vendor Management
Due: Before go-live
Security review: Passed (SOC 2 Type II, no exceptions)
Decision: Approved with conditions
```

---
*Training scenario from my SOC Triage Range practice tool. All organizations, people, and data are fictional.*
