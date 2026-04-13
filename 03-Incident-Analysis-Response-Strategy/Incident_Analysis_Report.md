# Incident Analysis Report: MGM Resorts 2023 Breach

## Executive Summary
In September 2023, MGM Resorts International fell victim to a sophisticated social engineering attack orchestrated by the threat group "Scattered Spider" (UNC3944). The breach resulted in a total operational shutdown of Las Vegas Strip properties for several days, leading to a financial impact of approximately **$100 million**. This incident serves as a primary case study for why "Identity is the New Perimeter."

## Impact Analysis (Evidence: SEC Form 8-K)
Based on the official SEC filing dated October 5, 2023:
* **Financial Impact:** $100M loss in EBITDAR + $10M in immediate remediation costs.
* **Operational Impact:** Occupancy fell to 88%; guest-facing systems (digital keys, slot machines, websites) were offline.
* **Data Privacy:** Personal Information (PII) of customers prior to March 2019 was compromised, including Driver's Licenses and some Social Security numbers.
* **Successful Controls:** Encryption and swift system isolation successfully prevented the theft of payment card industry (PCI) data and bank account details.

## Root Cause & Control Failure
The attack did not exploit a software bug. It exploited a **human process**:
1. **Vishing (Voice Phishing):** The attacker called the IT Helpdesk pretending to be an employee after gathering information from LinkedIn.
2. **Identity Verification Failure:** The Helpdesk agent bypassed standard verification protocols, allowing the attacker to reset the target's MFA (Multi-Factor Authentication).
3. **Privilege Escalation:** Once inside the Okta environment, the attacker gained Super Admin privileges, providing "keys to the kingdom."

## Tactical Mapping (MITRE ATT&CK)
| Phase | Technique ID | Description |
| :--- | :--- | :--- |
| **Initial Access** | T1566.004 | **Social Engineering:** Used Vishing to manipulate the IT helpdesk. |
| **Credential Access** | T1098 | **Account Manipulation:** Reset MFA to gain persistent access to the Okta tenant. |
| **Lateral Movement** | T1021 | **Remote Services:** Moved from the identity provider to the hypervisor (ESXi) environment. |
| **Impact** | T1486 | **Data Encrypted for Impact:** Deployment of ransomware across the server infrastructure. |



## Strategic Recommendations (The GRC Roadmap)
To prevent a similar "identity-based" breach, the following security controls are recommended:

### 1. Phishing-Resistant MFA (FIDO2)
* **Control:** Replace SMS and Push-based MFA with hardware security keys (e.g., FIDO2-compliant keys). 
* **Reasoning:** Unlike a 6-digit code, a physical key cannot be intercepted by a vishing attacker or bypassed through MFA fatigue.

### 2. Enhanced Helpdesk Verification Protocols
* **Control:** Implement a mandatory "Out-of-Band" verification policy.
* **Reasoning:** Helpdesk agents should be required to verify identities via a pre-registered work phone or via video verification by a direct supervisor before resetting MFA credentials.

### 3. Network Segmentation (OT vs. IT)
* **Control:** Strictly isolate Operational Technology (hotel locks, slot machines) from corporate IT environments.
* **Reasoning:** A compromise in the employee identity system should not provide lateral access to physical building controls or gaming floors.

---
**Analyst:** [Hayden]  
**Date:** April 13, 2026
