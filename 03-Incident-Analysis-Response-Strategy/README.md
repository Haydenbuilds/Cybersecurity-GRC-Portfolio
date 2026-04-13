# Project 03: Cyber Incident Analysis - The MGM Resorts Breach

## Project Overview
This project provides a comprehensive post-mortem analysis of the 2023 ransomware attack on MGM Resorts. The study focuses on reconstructing the **Incident Timeline** and identifying the specific failures in security operations and administrative controls that allowed the breach to escalate.

## Methodology
- **Frameworks:** Analysis conducted using the **Cyber Kill Chain** and **MITRE ATT&CK Framework**.
- **Incident Reconstruction:** Re-modeling the 7 stages of the attack from Initial Access to Impact.
- **Gap Analysis:** Comparing the victim's actual response against **NIST SP 800-61** (Computer Security Incident Handling Guide) standards.

## Key Highlights
- **Root Cause Analysis:** Identified the primary vulnerability as a failure in the IT Helpdesk's identity verification process (Vishing).
- **Tactical Mapping:** Mapped attacker movements to specific TTPs (Tactics, Techniques, and Procedures), including MFA fatigue and Okta tenant compromise.
- **Strategic Recommendations:** Developed a remediation roadmap prioritizing **FIDO2-based MFA** and enhanced Security Awareness Training (SAT) for high-privilege support roles.

## Deliverables
- **[Incident_Analysis_Report.md](./Incident_Analysis_Report.md):** A detailed technical breakdown of the breach and control failures.
- **[Incident_Timeline_Visual.png](./Incident_Timeline_Visual.png):** A high-level diagram illustrating the progression of the attack.
