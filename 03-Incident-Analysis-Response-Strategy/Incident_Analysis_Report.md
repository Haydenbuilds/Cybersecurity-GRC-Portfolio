# Incident Analysis Report: MGM Resorts 2023 Breach

## Executive Summary
In September 2023, MGM Resorts International fell victim to a sophisticated social engineering attack orchestrated by the threat group "Scattered Spider." The breach resulted in a total operational shutdown of Las Vegas Strip properties for several days, leading to a financial impact of approximately **$100 million**.

## Impact Analysis (Evidence: SEC Form 8-K)
Based on the official SEC filing dated October 5, 2023:
* **Financial Impact:** $100M loss in EBITDAR + $10M in immediate remediation costs.
* **Operational Impact:** Occupancy fell to 88%; guest-facing systems (digital keys, slot machines, websites) were offline.
* **Data Privacy:** Personal Information (PII) of customers prior to March 2019 was compromised, including Driver's Licenses and some Social Security numbers.
* **Successful Controls:** Encryption and swift system isolation successfully prevented the theft of payment card industry (PCI) data and bank account details.

## Root Cause & Control Failure
The attack did not exploit a software bug. It exploited a **human process**:
1. **Vishing (Voice Phishing):** The attacker called the IT Helpdesk pretending to be an employee.
2. **Identity Verification Failure:** The Helpdesk agent bypassed standard verification protocols, allowing the attacker to reset the target's MFA (Multi-Factor Authentication).
3. **Privilege Escalation:** Once inside the Okta environment, the attacker gained Super Admin privileges.
