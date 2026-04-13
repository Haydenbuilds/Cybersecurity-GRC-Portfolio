# Internal Memo: Security Assessment of Anthropic Claude AI Services

**To:** Cloud Governance Committee / CISO  
**From:** Hayden, Cybersecurity & GRC Analyst  
**Date:** April 2026  
**Subject:** Vendor Risk Review - Anthropic (Enterprise Deployment)
**Overall Risk Rating:** **LOW** (Approved with Conditions)

---

## 1. Introduction & Business Context
As the organization explores the integration of Generative AI to improve internal workflows, this report evaluates **Anthropic** as a Tier-1 vendor. This assessment specifically focuses on the **Claude for Enterprise** and **API** offerings. The primary goal is to ensure that proprietary source code and sensitive customer data (PII) remain protected in compliance with internal security standards and data protection laws.

## 2. Methodology & Evidence Base
This assessment was performed via an "Outside-In" analysis using Anthropic’s official Trust Center and the **Data Processing Addendum (DPA) effective Feb 2025**. Artifacts reviewed include:
- **SOC 3 Report (2025):** Verifying effective controls for Security, Availability, and Confidentiality.
- **FedRAMP High Authorization:** Demonstrating compliance with the most rigorous US Federal security standards.
- **ISO 27001:2022 Certification:** Proving a mature Information Security Management System (ISMS).

## 3. Detailed Control Analysis (Based on DPA & Trust Center)

### Data Privacy & Model Training (DPA Section B.3)
A critical concern for GRC is the potential for data leakage into public models. 
- **Finding:** Per the DPA, Anthropic contractually commits to **not** "sell" or "share" Customer Personal Data. Most importantly, data submitted through Enterprise/API tiers is **not** used to train foundation models.
- **Retention:** Anthropic commits to deleting Customer Data within **30 days** of contract termination (DPA Section H.1).

### Infrastructure Security (Schedule 2)
- **Encryption:** Data-at-rest is secured via **AES-256**; data-in-transit is secured via **TLS 1.2+**.
- **Endpoint Protection:** All Anthropic personnel workstations are protected via **EDR (Endpoint Detection and Response)** systems with 24/7 real-time monitoring.
- **Incident Response:** Anthropic guarantees written notification within **48 hours** of a confirmed Security Breach (DPA Section G.1).

### Subprocessor Management (Section C)
Anthropic leverages Tier-1 CSPs (**AWS, Google Cloud, and Azure**). They remain liable for the acts and omissions of their Subprocessors, ensuring a consistent security chain.

## 4. Shared Responsibility & Identified Risks
While Anthropic provides a secure environment, the organization must manage risks related to the **User Layer**:

1. **Prompt Injection:** Malicious or poorly designed inputs could lead to unintended data output or bypass safety filters.
2. **Shadow AI (Data Leakage):** Employees using personal accounts (Claude Free/Pro) instead of the Enterprise account risk having corporate data used for model training.

## 5. Formal Recommendation: CONDITIONAL APPROVAL

I recommend approval for enterprise deployment, subject to the following guardrails:

* **Corporate SSO Integration:** Mandatory login via Corporate IDP (Azure AD/Okta) to ensure instant access revocation upon employee offboarding.
* **Data Masking Policy:** Implement automated tools to redact PII/PHI before it is sent to the Anthropic API.
* **Log Ingestion:** Export Anthropic audit logs to our **SIEM (Splunk/Sentinel)** for proactive threat hunting and monitoring of "Shadow AI" activity.

---
## Supporting Evidence (Artifacts)
All reviewed documents are stored in the local repository for audit traceability:

1. **SOC 3 Report:** [View PDF](./Evidence/[Anthropic]_2025_Type_2_SOC_3_Report.pdf)
2. **ISO 27001 Certificate:** [View PDF](./Evidence/[Anthropic]_ISO_27001_Certificate_(2025).pdf)
3. **Data Processing Addendum:** [View PDF](./Evidence/[Anthropic]_DPA_2025.pdf)
4. **Trust Center Snapshot:** [View Image](./Evidence/Trust_Center_Snapshot.png)

---
**Analyst Signature:** *Hayden* *Cybersecurity & GRC Specialist*
