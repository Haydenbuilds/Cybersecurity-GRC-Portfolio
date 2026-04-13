# Incident Timeline: The 10-Minute Phone Call That Cost $100M

This timeline reconstructs the sequence of events during the September 2023 MGM Resorts breach, illustrating the speed at which social engineering can bypass multi-billion dollar security infrastructures.

| Time / Phase | Action | Details |
| :--- | :--- | :--- |
| **T-Minus 24 Hours** | **Reconnaissance** | Attackers (Scattered Spider) used LinkedIn to identify an MGM employee's name, title, and potential department. |
| **Minute 0** | **The Vishing Call** | The attacker called the MGM IT Helpdesk, impersonating the identified employee and claiming they lost access to their MFA device. |
| **Minute 10** | **The Breach** | The Helpdesk agent, following a weak verification protocol, reset the employee's password and registered a new MFA device controlled by the attacker. |
| **Day 1** | **Identity Takeover** | With initial access, the attacker pivoted to the Okta (Identity Provider) environment, gaining "Super Admin" privileges. |
| **Day 2-3** | **Lateral Movement** | Attackers moved from the cloud identity environment into the on-premise ESXi (Virtual Server) environment. |
| **Day 4** | **Impact & Ransom** | When MGM refused to pay the ransom, the attackers began shutting down systems and encrypting servers. |
| **Day 5+** | **Chaos** | Las Vegas properties went "dark." Digital room keys failed, slot machines displayed error messages, and manual check-ins began. |

---

## Technical Visual Representation


## Key Takeaway
This timeline demonstrates that the **Mean Time to Compromise (MTTC)** was less than 15 minutes. The delay between the initial breach and the total shutdown was caused by the attackers "dwelling" in the system to identify the most critical servers (ESXi) to maximize their leverage.

### GRC Perspective:
* **The Gap:** Lack of "Out-of-Band" verification at the Helpdesk.
* **The Fix:** Implementation of NIST 800-63B guidelines for digital identity and authentication.
