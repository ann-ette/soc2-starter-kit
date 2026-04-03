# Risk Register

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME] (Founder)

---

## Overview

This risk register identifies, assesses, and tracks risks specific to [YOUR APP], including infrastructure, security, compliance, and AI-specific threats. Risks are assessed using a likelihood × impact matrix and regularly reviewed.

<!-- CUSTOMIZE: Adjust risk list based on your technology stack and business model -->

---

## Risk Likelihood & Impact Scale

| Level | Likelihood | Impact |
|-------|-----------|--------|
| **1 - Low** | <10% annual probability | Financial loss <$10K, minimal reputation damage |
| **2 - Medium** | 10-50% annual probability | Financial loss $10K–$100K, moderate downtime/impact |
| **3 - High** | 50-90% annual probability | Financial loss >$100K, significant downtime/customer impact |
| **4 - Critical** | >90% annual probability | >$500K loss, major breach, regulatory action possible |

---

## Risk Assessment Matrix

```
           Impact
        1    2    3    4
L   1  [1]  [2]  [3]  [4]
I   2  [2]  [4]  [6]  [8]
K   3  [3]  [6]  [9] [12]
E   4  [4]  [8] [12] [16]

Priority: 1–4 = Monitor, 6–8 = Mitigate, 9–12 = Reduce, 12+ = Critical
```

---

## Worked Example: How to Score a Risk

This section walks through a realistic example of how to assess and score a single risk from start to finish.

### Example Scenario: Voice API Vendor Data Breach

Imagine your app integrates with a voice API vendor (e.g., ElevenLabs) to process user voice input. You need to assess the risk that this vendor suffers a data breach exposing conversation transcripts.

#### Step 1: Assess Likelihood

**What factors should you consider?**

- **Vendor's security posture:** Does the vendor have SOC 2 Type II certification? Have they had documented breaches in the past? Do they employ security best practices (encryption, access controls)?
- **Your data exposure:** How much customer data flows through this vendor? Is it encrypted in transit? Do they retain data indefinitely or auto-delete?
- **Industry trend:** How common are breaches in this type of vendor? (Voice APIs and LLM providers are frequently targeted.)
- **Contractual protections:** Do you have a Data Processing Agreement (DPA) that requires the vendor to notify you immediately if breached?

**Assessment:** Let's say the vendor has SOC 2 Type II, you encrypt data in transit, and they auto-delete after 30 days. But voice APIs are a frequent attack target. You estimate a 20% annual probability of a breach at this vendor. That maps to **Likelihood 2 (10–50%, Medium)**.

#### Step 2: Assess Impact

**What's the worst-case outcome if this vendor is breached?**

- **Financial impact:** Customer churn, regulatory fines, incident response costs. If 10% of users churn due to loss of trust, that might be $20K–$100K depending on your ARR.
- **Regulatory impact:** If you process voice data of EU residents, a breach is reportable under GDPR. Fines can reach 4% of global revenue (though usually much lower for vendors acting as processors).
- **Reputation impact:** Trust loss is hard to quantify but real. A breach at a AI/voice company is especially damaging.
- **Operational impact:** Brief service disruption if you need to cut off the vendor and migrate to an alternative.

**Assessment:** Worst case: regulatory fine (€10K–€50K range), customer churn ($20K–$50K lost ARR), incident costs ($5K–$10K). Total impact: $35K–$110K. That maps to **Impact 3 (High: $100K range)**.

#### Step 3: Calculate Risk Score

**Risk Score = Likelihood × Impact**

- Likelihood: 2 (Medium)
- Impact: 3 (High)
- **Risk Score = 2 × 3 = 6 (Mitigate Priority)**

From the risk matrix: Score 6 is in the "Mitigate" band. This risk needs a documented mitigation plan but is not critical.

#### Step 4: Design Mitigations

**What can you do to reduce either likelihood or impact (or both)?**

**Reduce Likelihood** (make the breach less likely):
- Require vendor to have SOC 2 Type II (already done)
- Audit vendor's security practices annually
- Request their latest SOC 2 audit report
- Ensure DPA includes audit rights and breach notification SLA

**Reduce Impact** (limit damage if breach does happen):
- Minimize data retention at vendor: Configure voice API to auto-delete after 7 days instead of 30
- Encrypt data before sending to vendor (if possible)
- Have a vendor contingency plan: contract with 2-3 alternative voice API vendors so you can switch within hours
- Communicate transparently with users: Have a breach notification template ready
- Insurance: Consider cyber insurance that covers vendor breaches

**Implementation:** You decide to (1) require SOC 2, (2) auto-delete after 7 days, (3) sign a strong DPA, and (4) contract with 2 alternatives. These mitigations meaningfully reduce both likelihood and impact.

#### Step 5: Calculate Residual Risk

**After mitigations, what's the residual (remaining) risk?**

With mitigations in place:
- **Residual Likelihood:** Reduced from 20% to 5% (due to audit requirements, strong DPA, 7-day retention). **Now Likelihood 1 (Low)**.
- **Residual Impact:** Reduced from $100K to $30K (smaller window of exposure due to 7-day retention, alternatives on standby). **Now Impact 2 (Medium)**.
- **Residual Risk Score = 1 × 2 = 2 (Monitor Priority)**

The risk dropped from 6 (Mitigate) to 2 (Monitor). You've successfully brought it under control.

#### Step 6: Document Evidence

**What proof do you have that these mitigations are in place?**

- DPA agreement signed with vendor (store in compliance folder)
- Vendor's latest SOC 2 Type II audit report (obtain and store)
- API configuration showing 7-day auto-delete (screenshot or config file)
- Contracts with 2 alternative vendors signed
- Breach notification template drafted and approved
- Annual vendor audit scheduled (calendar event + log)

All of this evidence is what an auditor will ask for. Document it continuously, don't scramble to find it during audit prep.

#### Key Takeaways from This Example

1. **Assess likelihood realistically**, not pessimistically. Use industry data, vendor track records, and your specific controls.
2. **Impact assessment is concrete.** Quantify it: customer churn, regulatory fine, incident cost. Put a number on it.
3. **Mitigations reduce the score.** The point of the risk register is to drive action. Pick mitigations that actually move the needle (not checkbox exercises).
4. **Residual risk is what matters.** Even a critical risk (score 12) becomes acceptable if you can mitigate it to a 3.
5. **Evidence is everything.** You won't remember why you made a decision in 6 months. Document it now so auditors (and you) can verify later.

---

## Active Risk Register

### 1. Data Breach / Unauthorized Access to Customer Data

| Field | Value |
|-------|-------|
| **ID** | RISK-001 |
| **Risk Statement** | Unauthorized access to customer data stored in [YOUR DATABASE] could expose PII, conversation history, and biometric/voice data |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 4 (Critical: regulatory fine, customer loss, reputation damage) |
| **Risk Score** | 8 (High Priority) |
| **Affected Asset** | [YOUR DATABASE], S3/[YOUR CLOUD PROVIDER] storage |
| **Mitigations** | • Encryption at rest (AES-256) and in transit (TLS 1.2+)<br/>• IAM policy: least privilege access<br/>• Regular access audits and log monitoring<br/>• Database activity monitoring alerts<br/>• MFA for all admin accounts |
| **Evidence/Control** | • AWS/[YOUR CLOUD PROVIDER] Config rules<br/>• Monthly access review reports<br/>• Encryption key management policy<br/>• Firewall rules / security groups |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 2. Prompt Injection Attack (AI-Specific Risk)

| Field | Value |
|-------|-------|
| **ID** | RISK-002 |
| **Risk Statement** | Attackers craft malicious prompts to bypass system instructions, exfiltrate training data, or cause model to generate harmful content |
| **Likelihood** | 3 (High: 50–90%) |
| **Impact** | 3 (High: reputation damage, service disruption, potential liability) |
| **Risk Score** | 9 (Critical Priority) |
| **Affected Asset** | LLM API integration, prompt handling logic |
| **Mitigations** | • Input validation and sanitization on all user prompts<br/>• System prompt hardening (no direct concatenation)<br/>• Rate limiting per user/IP<br/>• Output filtering and content moderation<br/>• User prompt logging and anomaly detection<br/>• Regular red-teaming exercises |
| **Evidence/Control** | • Input validation code review<br/>• Security test cases for prompt injection<br/>• Monitoring dashboard for unusual query patterns<br/>• Annual red-teaming report |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 3. Model Training Data Leakage (AI-Specific Risk)

| Field | Value |
|-------|-------|
| **ID** | RISK-003 |
| **Risk Statement** | Customer conversation data or proprietary information inadvertently included in fine-tuning/training data leaks or is exposed via model output (e.g., through prompt injection or model memorization) |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 4 (Critical: customer trust loss, regulatory action, IP theft) |
| **Risk Score** | 8 (High Priority) |
| **Affected Asset** | LLM vendor training infrastructure, fine-tuning pipeline |
| **Mitigations** | • Explicit data processing agreements with LLM vendors<br/>• Data anonymization before any training use<br/>• Opt-out mechanisms for customers<br/>• Regular vendor audit of training data usage<br/>• No PII in model prompts/training<br/>• Version control and data lineage tracking |
| **Evidence/Control** | • Vendor DPA signed by [DATE]<br/>• Data classification and handling policy<br/>• Training data audit logs<br/>• Privacy impact assessment |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 4. Voice/Biometric Data Misuse or Leakage (AI-Specific Risk)

| Field | Value |
|-------|-------|
| **ID** | RISK-004 |
| **Risk Statement** | Voice recordings or biometric samples (if collected) are exposed, sold, or used for unauthorized purposes (e.g., deepfake generation, unauthorized authentication) |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 4 (Critical: regulatory action, GDPR/CCPA fines, identity theft) |
| **Risk Score** | 8 (High Priority) |
| **Affected Asset** | Voice API provider, storage for audio files, [YOUR DATABASE] |
| **Mitigations** | • Strict consent and opt-in for voice collection<br/>• Separate encrypted storage for voice/biometric data<br/>• Automatic deletion after [X] days<br/>• No use of voice data for training without explicit consent<br/>• Vendor assessment of biometric safeguards<br/>• User ability to request deletion anytime |
| **Evidence/Control** | • Privacy policy and consent flows<br/>• Voice API vendor security assessment<br/>• Automated deletion schedules and logs<br/>• Privacy impact assessment |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 5. Multi-Vendor Data Pipeline Risk (AI-Specific Risk)

| Field | Value |
|-------|-------|
| **ID** | RISK-005 |
| **Risk Statement** | Customer data flows through multiple third-party APIs/vendors (LLM provider, voice service, analytics). Loss of vendor security posture or breach at any link exposes data. |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 3 (High: service interruption, data breach, customer loss) |
| **Risk Score** | 6 (Mitigate) |
| **Affected Asset** | All third-party APIs and integrations |
| **Mitigations** | • Vendor security assessment and SOC 2 verification<br/>• Data Processing Agreements (DPAs) signed with all vendors<br/>• Minimize data sharing (only essential fields)<br/>• Regular vendor audit and compliance check<br/>• Incident response plan for vendor breach<br/>• Quarterly vendor risk review |
| **Evidence/Control** | • Subprocessor inventory (SUBPROCESSOR-TABLE.md)<br/>• Signed DPAs with all vendors<br/>• Vendor assessment questionnaire responses<br/>• Quarterly vendor review log |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 6. Insecure API Implementation / Authentication Bypass

| Field | Value |
|-------|-------|
| **ID** | RISK-006 |
| **Risk Statement** | Weak API authentication, missing rate limiting, or improper authorization allows unauthorized access to [YOUR APP] APIs or customer data |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 3 (High: data exposure, service abuse, reputation) |
| **Risk Score** | 6 (Mitigate) |
| **Affected Asset** | API endpoints, authentication layer |
| **Mitigations** | • OAuth 2.0 / JWT with short expiration<br/>• MFA for sensitive operations<br/>• Rate limiting per API key/IP<br/>• API key rotation schedule (quarterly)<br/>• CORS policy hardening<br/>• Regular security code review and OWASP testing |
| **Evidence/Control** | • API security policy document<br/>• Code review checklist<br/>• Automated security testing in CI/CD<br/>• API usage logs and anomaly alerts |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 7. Supply Chain Attack / Dependency Vulnerability

| Field | Value |
|-------|-------|
| **ID** | RISK-007 |
| **Risk Statement** | Compromised or vulnerable open-source dependencies in [YOUR APP] codebase allow code execution or data exfiltration |
| **Likelihood** | 3 (High: 50–90%) |
| **Impact** | 3 (High: code compromise, service interruption) |
| **Risk Score** | 9 (Critical Priority) |
| **Affected Asset** | Application codebase, CI/CD pipeline |
| **Mitigations** | • Dependency scanning tool (Dependabot, Snyk) enabled<br/>• Weekly dependency update reviews<br/>• Bill of Materials (SBOM) maintained<br/>• License scanning for GPL/copyleft<br/>• Signed commits required<br/>• Vendor verification for critical packages |
| **Evidence/Control** | • Dependabot/Snyk scan reports<br/>• SBOM artifact in release<br/>• Git history of dependency updates<br/>• Security advisory response log |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 8. Inadequate Access Control / Role-Based Access Missing

| Field | Value |
|-------|-------|
| **ID** | RISK-008 |
| **Risk Statement** | Employees or contractors have overly broad permissions; no role-based access control (RBAC) implemented for admin functions, data exports |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 3 (High: data theft by insider, compliance violation) |
| **Risk Score** | 6 (Mitigate) |
| **Affected Asset** | Admin dashboards, [YOUR DATABASE], [YOUR CLOUD PROVIDER] IAM |
| **Mitigations** | • Role-based access control (RBAC) for all admin functions<br/>• Least-privilege principle enforced<br/>• Monthly access certification by manager<br/>• Audit logging of all admin actions<br/>• Background checks for employees with data access<br/>• Offboarding checklist with revoked access |
| **Evidence/Control** | • IAM policy documentation<br/>• Access review and certification reports (monthly)<br/>• Audit logs query capability<br/>• Offboarding checklist |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 9. Inadequate Logging / Insufficient Audit Trail

| Field | Value |
|-------|-------|
| **ID** | RISK-009 |
| **Risk Statement** | Insufficient logging of critical events prevents detection of breaches, makes incident investigation impossible, and violates audit requirements |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 3 (High: undetected breach, regulatory non-compliance) |
| **Risk Score** | 6 (Mitigate) |
| **Affected Asset** | Application logs, database logs, API gateway logs, [YOUR CLOUD PROVIDER] CloudTrail |
| **Mitigations** | • Centralized logging (CloudWatch, ELK, Datadog)<br/>• Log retention policy (minimum 90 days, 1 year for audit)<br/>• Immutable log storage<br/>• Real-time alerting for security events<br/>• Regular log review and audit<br/>• Log analysis for anomaly detection |
| **Evidence/Control** | • Logging policy documentation<br/>• Log retention and archival schedule<br/>• Alert configuration and response procedures<br/>• Sample logs from production environment |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 10. Lack of Encryption / Weak Encryption

| Field | Value |
|-------|-------|
| **ID** | RISK-010 |
| **Risk Statement** | Data at rest or in transit not encrypted, or weak encryption algorithms used; encryption keys not properly managed |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 4 (Critical: data exposure, regulatory violation) |
| **Risk Score** | 8 (High Priority) |
| **Affected Asset** | [YOUR DATABASE], storage buckets, API communications, backups |
| **Mitigations** | • AES-256 encryption at rest for all databases<br/>• TLS 1.2+ for all data in transit<br/>• Certificate management and auto-renewal<br/>• Key rotation schedule (annually)<br/>• Hardware Security Module (HSM) for key storage<br/>• Encryption key access controls |
| **Evidence/Control** | • Encryption policy documentation<br/>• TLS certificate inventory and renewal log<br/>• Key rotation audit trail<br/>• Database encryption verification report |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 11. Inadequate Incident Response / Breach Notification Plan

| Field | Value |
|-------|-------|
| **ID** | RISK-011 |
| **Risk Statement** | No documented incident response plan; delayed breach notification violates GDPR (72 hours), CCPA, and state breach notification laws |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 4 (Critical: regulatory fines, legal action) |
| **Risk Score** | 8 (High Priority) |
| **Affected Asset** | All systems |
| **Mitigations** | • Incident Response Plan documented<br/>• Breach notification procedure and legal contact identified<br/>• Incident response team assigned<br/>• Notification templates and timelines established<br/>• Annual incident response drill/tabletop<br/>• Post-incident review process |
| **Evidence/Control** | • Incident Response Plan document<br/>• Contact list and escalation procedures<br/>• Drill test records and lessons learned<br/>• Post-incident review samples |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 12. Unpatched Servers / Missing Security Updates

| Field | Value |
|-------|-------|
| **ID** | RISK-012 |
| **Risk Statement** | OS, application, or dependency vulnerabilities unpatched; no patch management schedule |
| **Likelihood** | 3 (High: 50–90%) |
| **Impact** | 3 (High: code execution, service disruption) |
| **Risk Score** | 9 (Critical Priority) |
| **Affected Asset** | Servers, containers, application dependencies |
| **Mitigations** | • Automated patch management ([YOUR CLOUD PROVIDER] Systems Manager, Renovate)<br/>• Monthly security update schedule<br/>• Critical patches within 7 days<br/>• Pre-production testing before rollout<br/>• Version pinning with automated update checks<br/>• Vulnerability scanning in CI/CD |
| **Evidence/Control** | • Patch schedule and tracking log<br/>• Automated vulnerability scan reports (weekly)<br/>• Release notes documenting patch dates<br/>• Container image scanning results |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 13. Inadequate Data Backup / Disaster Recovery

| Field | Value |
|-------|-------|
| **ID** | RISK-013 |
| **Risk Statement** | Backups missing, corrupted, or unencrypted; no tested recovery procedure; long RTO/RPO impacts customer data and service availability |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 3 (High: data loss, prolonged downtime) |
| **Risk Score** | 6 (Mitigate) |
| **Affected Asset** | [YOUR DATABASE], application state, configuration |
| **Mitigations** | • Daily encrypted backups to [YOUR CLOUD PROVIDER]<br/>• Backups stored in separate region<br/>• Automated backup verification and integrity checks<br/>• Quarterly disaster recovery drill with full recovery test<br/>• RTO = [X hours], RPO = [X hours]<br/>• Backup retention policy: [X] years |
| **Evidence/Control** | • Backup schedule and retention policy<br/>• DR drill test results and recovery time logs<br/>• Backup encryption and storage documentation<br/>• Database recovery test report (quarterly) |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 14. GDPR / CCPA Non-Compliance

| Field | Value |
|-------|-------|
| **ID** | RISK-014 |
| **Risk Statement** | [YOUR APP] handles EU/California resident data but lacks GDPR/CCPA controls (e.g., data export, deletion, consent management) |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 4 (Critical: up to 4% global revenue or €20M in fines) |
| **Risk Score** | 8 (High Priority) |
| **Affected Asset** | [YOUR DATABASE], user dashboards, data handling processes |
| **Mitigations** | • Privacy policy aligned with GDPR/CCPA<br/>• Data subject access request (DSAR) process<br/>• Right-to-deletion functionality<br/>• Consent management system<br/>• Data Processing Agreement with customers<br/>• Privacy Impact Assessment (PIA)<br/>• Data Protection Officer contact |
| **Evidence/Control** | • Privacy policy (dated)<br/>• Privacy Impact Assessment document<br/>• DSAR response procedure and log<br/>• Consent records and audit trail |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

### 15. Inadequate Vendor Security Management

| Field | Value |
|-------|-------|
| **ID** | RISK-015 |
| **Risk Statement** | Third-party vendors lack SOC 2 certification, DPA, or security controls; vendor breach cascades to [YOUR APP] and customers |
| **Likelihood** | 2 (Medium: 10–50%) |
| **Impact** | 3 (High: breach, service interruption, compliance violation) |
| **Risk Score** | 6 (Mitigate) |
| **Affected Asset** | All third-party integrations (LLM, voice, payment, hosting) |
| **Mitigations** | • Subprocessor assessment before integration<br/>• SOC 2 Type II or equivalent certification required<br/>• Signed Data Processing Agreement (DPA)<br/>• Annual vendor risk review<br/>• Incident notification clause in contracts<br/>• Right to audit vendor security practices |
| **Evidence/Control** | • Subprocessor inventory (SUBPROCESSOR-TABLE.md)<br/>• Vendor assessment questionnaires<br/>• Signed DPAs with all vendors<br/>• Annual vendor audit reports |
| **Remediation Owner** | [YOUR NAME] |
| **Remediation Due** | [DATE] |
| **Status** | In Progress |
| **Last Reviewed** | [DATE] |

---

## Risk Review Schedule

<!-- CUSTOMIZE: Adjust review frequency based on your risk tolerance -->

- **Quarterly:** Full risk register review and scoring update
- **Monthly:** Review of "In Progress" remediation items
- **Incident-Driven:** Add/update risks immediately after incident detection
- **Annually:** Complete risk reassessment with leadership and security team

---

## Risk Escalation Procedures

| Risk Score | Action | Responsible | Timeline |
|-----------|--------|-------------|----------|
| 1–4 | Monitor and document | [YOUR NAME] (Founder) | Quarterly |
| 6–8 | Develop mitigation plan | [YOUR NAME] (Founder) | 2 weeks |
| 9–12 | Immediate remediation | [YOUR NAME] (Founder) | 1 week |
| 12+ | Critical escalation + incident response | [YOUR NAME] (Founder) | 24 hours |

---

## Change Log

| Date | Change | Owner |
|------|--------|-------|
| [DATE] | Initial risk register | [YOUR NAME] |
| [DATE] | Updated risk scoring post-incident | [YOUR NAME] |

---

## Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| [YOUR NAME] (Founder) | [YOUR NAME] | _____________ | ________ |

**Solo founders:** Sign this line to indicate you've reviewed and accepted responsibility for managing the identified risks and implementing mitigations.
