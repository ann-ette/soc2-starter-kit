# Subprocessor / Vendor Inventory

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME], Compliance Lead

---

## Team Size Adaptation

This template uses role names like "Compliance Lead" as a placeholder. For solo founders, you fill all these roles yourself — simply use your own name. For small teams (2–5), assign roles based on who handles vendor relationships. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This document maintains an inventory of all third-party vendors and subprocessors that handle customer data on behalf of [YOUR COMPANY]. Each vendor is assessed for security posture, compliance certifications, and data handling practices. This inventory is shared with customers as required by GDPR Article 28 (Data Processing Agreements).

<!-- CUSTOMIZE: Update this list for your specific vendors -->

---

## Subprocessor Inventory

| Vendor Name | Service Category | Data Shared | Purpose | Data Retention | SOC 2 Status | DPA Signed | Risk Level | Last Reviewed | Status |
|-------------|-----------------|------------|---------|---|---|---|---|---|---|
| **OpenAI** | LLM / API | Anonymized conversation text, user ID (hashed) | Generate AI responses | 30 days (per OpenAI policy) | Type II | Yes, 2026-01-15 | Medium | 2026-03-15 | ✓ Active |
| **Twilio** | Voice / SMS API | Phone numbers, voice recordings, transcripts | Voice interaction, SMS delivery | 7 days | Type II | Yes, 2025-11-20 | Medium | 2026-02-01 | ✓ Active |
| **Stripe** | Payment Processor | Card last-4, billing name/address, email | Process payments | 7 years (PCI compliance) | Type II | Yes, 2025-10-30 | High | 2026-03-20 | ✓ Active |
| **AWS** | Cloud Infrastructure | All application data, backups, logs | Hosting, storage, compute | Per retention policy | Type II | Yes, 2025-09-01 | High | 2026-03-10 | ✓ Active |
| **Google Analytics** | Analytics | Anonymized user behavior, IP (masked), device type | Track feature usage | 24 months | Type II | Yes, 2026-02-10 | Low | 2026-02-10 | ✓ Active |
| **Auth0** | Authentication | Email, password hash, MFA tokens | User authentication | Until account deletion | Type II | Pending | Medium | 2026-02-20 | ⚠ Pending DPA |
| **SendGrid** | Email Service | Email addresses, user ID | Transactional email | Until bounce/unsubscribe | Type II | Yes, 2025-12-05 | Low | 2026-01-30 | ✓ Active |
| **Datadog** | Monitoring / Logging | Application logs, performance metrics, user IDs (anonymized) | System monitoring, alerting | 90 days (hot), 1 year (archive) | Type II | Yes, 2026-03-01 | Medium | 2026-03-01 | ✓ Active |
| **GitHub** | Code Repository | Source code, contributor emails | Version control | Until repository deletion | SOC 2 Type II | Yes, 2025-08-15 | High | 2026-02-15 | ✓ Active |
| **[FUTURE] Anthropic** | LLM / Fine-tuning | Conversation data (with consent) | Model fine-tuning | [TBD - under evaluation] | Type II | Pending | High | 2026-04-01 | ⏳ Evaluating |

---

## Vendor Details & Risk Assessment

### 1. OpenAI (LLM)

| Field | Value |
|-------|-------|
| **Vendor** | OpenAI, Inc. |
| **Service** | LLM API (GPT-4, GPT-3.5-Turbo) |
| **Data Shared** | User conversation text (anonymized), metadata (user_id hashed, timestamps) |
| **Purpose** | Generate AI responses to user prompts |
| **API Endpoint** | https://api.openai.com/v1/chat/completions |
| **Data Retention** | 30 days default (OpenAI uses for system improvement); can request no retention via enterprise agreement |
| **Deletion Capability** | Manual request to OpenAI; enterprise customers can opt-out of data retention |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, OpenAI infrastructure |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | Signed 2026-01-15 |
| **Sub-processors** | OpenAI may use cloud providers (AWS, Azure) for infrastructure |
| **Audit Access** | Limited; OpenAI provides security questionnaire responses |
| **Security Certifications** | ISO 27001, SOC 2 Type II |
| **Incident Notification** | Per DPA (typically 48 hours) |
| **Data Location** | US data centers (default) |
| **Risk Level** | **Medium** (industry-standard LLM vendor, but largest data recipient) |
| **Mitigations** | • Anonymize user data before sending<br/>• Use hashed user IDs only<br/>• Monitor OpenAI status page for incidents<br/>• Regular vendor security reviews<br/>• Alternative LLM vendors identified for contingency |
| **Last Security Review** | 2026-03-15 (quarterly review) |
| **Next Review** | 2026-06-15 |
| **Status** | ✓ Active & Approved |

**Training Data Usage:** OpenAI does NOT use API data for model training unless:
- Enterprise agreement explicitly allows it
- Customer provides explicit consent
- Data is anonymized beyond re-identification

**Current Status:** Data is NOT used for training. Confirm annually with OpenAI.

---

### 2. Twilio (Voice / SMS)

| Field | Value |
|-------|-------|
| **Vendor** | Twilio Inc. |
| **Service** | Voice API, SMS API, Programmable Voice |
| **Data Shared** | Phone numbers, voice recordings (audio files), transcriptions |
| **Purpose** | Enable voice calls and SMS interactions in [YOUR APP] |
| **Data Retention** | 7 days (voice recordings); 30 days (call logs) |
| **Deletion Capability** | Automatic deletion after retention period |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Twilio infrastructure |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | Signed 2025-11-20 |
| **Sub-processors** | Twilio uses AWS infrastructure |
| **Audit Access** | Limited; vendor assessment questionnaire completed |
| **Security Certifications** | ISO 27001, SOC 2 Type II, HIPAA BAA available |
| **Incident Notification** | Per DPA (typically 24 hours) |
| **Data Location** | US data centers (configurable) |
| **Risk Level** | **Medium** (voice/audio data is sensitive; Twilio handles millions of calls securely) |
| **Mitigations** | • Separate storage for audio files (encrypted)<br/>• Auto-delete voice recordings after 7 days<br/>• Monitor Twilio incidents and security advisories<br/>• Review retention logs monthly<br/>• User consent obtained before voice recording |
| **Last Security Review** | 2026-02-01 (quarterly review) |
| **Next Review** | 2026-05-01 |
| **Status** | ✓ Active & Approved |

**Data Deletion Verification:** Monthly task to confirm 7-day auto-deletion is working.

---

### 3. Stripe (Payment)

| Field | Value |
|-------|-------|
| **Vendor** | Stripe Inc. |
| **Service** | Payment Processing, Billing |
| **Data Shared** | Card last-4 digits, billing name, address, email, payment amount, transaction ID |
| **Purpose** | Process customer payments, generate invoices |
| **Data Retention** | 7 years (PCI DSS compliance requirement) |
| **Deletion Capability** | Customer can request card deletion; Stripe retains transaction records per PCI/legal requirements |
| **Encryption In-Transit** | Yes, TLS 1.2+, PCI DSS Level 1 |
| **Encryption At-Rest** | Yes, tokenization (card data never stored in [YOUR DATABASE]) |
| **PCI DSS Compliance** | Yes, Level 1 (annual penetration testing, annual QSA assessment) |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | Signed 2025-10-30 |
| **Sub-processors** | Stripe uses AWS, Google Cloud for infrastructure |
| **Audit Access** | Limited; Stripe provides annual compliance reports |
| **Security Certifications** | PCI DSS Level 1, ISO 27001, SOC 2 Type II |
| **Incident Notification** | Per DPA (typically 24 hours) |
| **Data Location** | US data centers (configurable per regional requirements) |
| **Risk Level** | **High** (payment data = financial/identity risk; Stripe handles mitigation through PCI DSS) |
| **Mitigations** | • Use Stripe tokenization (never store full card numbers)<br/>• Webhook signature validation for all Stripe events<br/>• Monitor Stripe security advisories<br/>• Annual PCI DSS compliance audit<br/>• Incident response plan for payment processor breach<br/>• 3-D Secure enabled for high-risk transactions |
| **Last Security Review** | 2026-03-20 (quarterly review) |
| **Next Review** | 2026-06-20 |
| **Status** | ✓ Active & Approved |

**PCI Compliance:** [YOUR COMPANY] is PCI DSS compliant (Level 2 via Stripe Level 1 certification). Annual self-assessment performed.

---

### 4. AWS (Infrastructure)

| Field | Value |
|-------|-------|
| **Vendor** | Amazon Web Services, Inc. |
| **Service** | EC2, RDS, S3, CloudWatch, IAM, VPC |
| **Data Shared** | **ALL** application data (database, backups, logs, configuration) |
| **Purpose** | Cloud hosting, storage, compute, disaster recovery |
| **Data Retention** | Per [YOUR COMPANY] retention policy (see DATA-RETENTION-POLICY.md) |
| **Deletion Capability** | Yes, AWS provides deletion APIs and deletion verification |
| **Encryption In-Transit** | Yes, TLS 1.2+, VPN/VPC isolation |
| **Encryption At-Rest** | Yes, AES-256 (KMS managed keys) |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | Signed 2025-09-01 (AWS Service Terms + Data Protection Addendum) |
| **Sub-processors** | AWS partners with third-party vendors for specific services (S3 durability partners) |
| **Audit Access** | Yes, AWS Security Hub for compliance audits; AWS Artifact for SOC 2 reports |
| **Security Certifications** | SOC 2 Type II, ISO 27001, PCI DSS, HIPAA, FedRAMP |
| **Incident Notification** | AWS Security Bulletins (proactive); incident communication via AWS console |
| **Data Location** | [YOUR CLOUD PROVIDER] region (<!-- CUSTOMIZE: e.g., us-east-1 -->) |
| **Risk Level** | **High** (hosts all data; AWS security posture is mature and industry-leading) |
| **Mitigations** | • AWS Config rules for compliance monitoring<br/>• VPC security groups and NACLs<br/>• IAM least-privilege policies<br/>• KMS encryption for sensitive data<br/>• Automated backups and cross-region replication<br/>• AWS Security Hub monitoring<br/>• Quarterly AWS security assessment<br/>• Incident response runbook for AWS breach |
| **Last Security Review** | 2026-03-10 (quarterly review) |
| **Next Review** | 2026-06-10 |
| **Status** | ✓ Active & Approved |

**Multi-AZ & Disaster Recovery:** Production infrastructure spans 2 AZs; automatic failover configured.

---

### 5. Google Analytics

| Field | Value |
|-------|-------|
| **Vendor** | Google LLC |
| **Service** | Google Analytics 4 (GA4) |
| **Data Shared** | Anonymized user behavior (page views, clicks), anonymized IP address (masked), device type, referrer |
| **Purpose** | Track feature usage, understand user behavior, product analytics |
| **Data Retention** | 24 months (Google Analytics default) |
| **Deletion Capability** | Google provides aggregation/anonymization; individual user data cannot be deleted (anonymized) |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Google infrastructure |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | Signed 2026-02-10 (Google Cloud Terms + Data Protection Addendum) |
| **Sub-processors** | Google Cloud infrastructure |
| **Audit Access** | Limited; Google provides privacy control documentation |
| **Security Certifications** | SOC 2 Type II, ISO 27001, GDPR compliant |
| **Incident Notification** | Google Security Bulletin (proactive advisories) |
| **Data Location** | US data centers (configurable) |
| **Risk Level** | **Low** (data is anonymized and aggregated; no PII transmitted) |
| **Mitigations** | • Enable IP anonymization in GA4<br/>• Exclude internal IPs from analytics<br/>• Regular privacy policy update to disclose GA4 usage<br/>• Monitor Google privacy documentation for changes |
| **Last Security Review** | 2026-02-10 (quarterly review) |
| **Next Review** | 2026-05-10 |
| **Status** | ✓ Active & Approved |

**GDPR Compliance:** Data processed is anonymized; GDPR DPA in place.

---

### 6. Auth0 (Authentication) ⚠ Pending DPA

| Field | Value |
|-------|-------|
| **Vendor** | Auth0, Inc. (owned by Okta) |
| **Service** | Authentication (OAuth 2.0, SAML, passwordless) |
| **Data Shared** | Email address, password hash (Auth0-managed), MFA tokens, last login date |
| **Purpose** | User authentication, identity management, MFA |
| **Data Retention** | Until user account deletion |
| **Deletion Capability** | Auth0 provides account deletion API |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Auth0 infrastructure (Okta) |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | **PENDING** (DPA draft received; legal review in progress) |
| **Sub-processors** | Okta infrastructure, Auth0 managed services |
| **Audit Access** | Limited; vendor assessment questionnaire in progress |
| **Security Certifications** | SOC 2 Type II, ISO 27001 |
| **Incident Notification** | Per DPA (once signed) |
| **Data Location** | US data centers |
| **Risk Level** | **Medium** (authentication = critical access control; Auth0 is industry-standard but DPA pending) |
| **Status** | ⚠ **Pending DPA Signature** (do not send customer data until DPA signed) |

**Action Items:**
- [ ] Negotiate DPA with Auth0 legal team (due: 2026-05-01)
- [ ] Sign DPA once approved by legal
- [ ] Update this table with signed date
- [ ] Notify customers of Auth0 integration once DPA signed
- **Interim Mitigation:** Only enable Auth0 for internal testing; customers should use alternative auth method until DPA signed

---

### 7. SendGrid (Email)

| Field | Value |
|-------|-------|
| **Vendor** | Twilio SendGrid |
| **Service** | Transactional Email, Email Delivery |
| **Data Shared** | Customer email addresses, email content (transactional only), user ID |
| **Purpose** | Send transactional emails (password reset, receipts, alerts) |
| **Data Retention** | Until bounce or unsubscribe; log retention 90 days |
| **Deletion Capability** | Auto-delete bounced/unsubscribed email addresses; manual suppression lists |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Twilio infrastructure |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | Signed 2025-12-05 |
| **Sub-processors** | Twilio infrastructure |
| **Audit Access** | Limited; vendor assessment completed |
| **Security Certifications** | SOC 2 Type II, ISO 27001 |
| **Incident Notification** | Per DPA (typically 24 hours) |
| **Data Location** | US data centers |
| **Risk Level** | **Low** (transactional email only; no customer data in body) |
| **Mitigations** | • Only send transactional emails (no customer data in body)<br/>• Comply with CAN-SPAM requirements<br/>• Monitor SendGrid bounce/complaint rates<br/>• Unsubscribe link in all emails<br/>• Monitor SendGrid status page for incidents |
| **Last Security Review** | 2026-01-30 (quarterly review) |
| **Next Review** | 2026-04-30 |
| **Status** | ✓ Active & Approved |

---

### 8. Datadog (Monitoring)

| Field | Value |
|-------|-------|
| **Vendor** | Datadog, Inc. |
| **Service** | Application Performance Monitoring (APM), Log Management, Alerting |
| **Data Shared** | Application logs (may contain user IDs, anonymized), performance metrics, error traces |
| **Purpose** | Monitor application health, incident detection, performance analysis |
| **Data Retention** | 90 days (hot storage), 1 year (archive/cold storage) |
| **Deletion Capability** | Automatic purge per retention policy; manual deletion available |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Datadog infrastructure |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | Signed 2026-03-01 |
| **Sub-processors** | AWS, Google Cloud infrastructure |
| **Audit Access** | Yes, Datadog Security & Compliance dashboard |
| **Security Certifications** | SOC 2 Type II, ISO 27001, HIPAA BAA available |
| **Incident Notification** | Datadog security advisories and status page |
| **Data Location** | US data centers (configurable) |
| **Risk Level** | **Medium** (logs may contain anonymized user IDs; Datadog is industry-standard) |
| **Mitigations** | • Anonymize user IDs in logs before sending to Datadog<br/>• Monitor Datadog retention policies<br/>• Review sampled logs for PII leakage quarterly<br/>• Monitor Datadog status page for incidents |
| **Last Security Review** | 2026-03-01 (quarterly review) |
| **Next Review** | 2026-06-01 |
| **Status** | ✓ Active & Approved |

---

### 9. GitHub (Code Repository)

| Field | Value |
|-------|-------|
| **Vendor** | GitHub, Inc. (owned by Microsoft) |
| **Service** | Git Repository, CI/CD (GitHub Actions), Secrets Management |
| **Data Shared** | Source code (public and private), contributor emails, CI/CD secrets, deployment logs |
| **Purpose** | Version control, code collaboration, automated testing/deployment |
| **Data Retention** | Until repository deletion or 2+ years of history |
| **Deletion Capability** | Repository deletion available; history removal requires force-push (not recommended) |
| **Encryption In-Transit** | Yes, TLS 1.2+, SSH key support |
| **Encryption At-Rest** | Yes, GitHub/Microsoft infrastructure |
| **SOC 2 Certification** | Type II (valid through [DATE]) |
| **DPA Status** | Signed 2025-08-15 (GitHub Enterprise Agreement includes DPA) |
| **Sub-processors** | Microsoft Azure infrastructure |
| **Audit Access** | GitHub Enterprise features; audit logs available |
| **Security Certifications** | SOC 2 Type II, ISO 27001, FedRAMP |
| **Incident Notification** | GitHub Security Advisories and Incident Reports |
| **Data Location** | US data centers (configurable for enterprise) |
| **Risk Level** | **High** (source code = IP; GitHub security is mature but code exposure risk if repository breached) |
| **Mitigations** | • Private repository (not public)<br/>• Branch protection rules (require code review)<br/>• Signed commits required (enforce GPG signing)<br/>• Secrets scanning enabled (detects hardcoded secrets)<br/>• Dependabot for vulnerability scanning<br/>• Regular audit of repository access permissions<br/>• No hardcoded secrets in git history (use GitHub Secrets for CI/CD)<br/>• Incident response plan for repository compromise |
| **Last Security Review** | 2026-02-15 (quarterly review) |
| **Next Review** | 2026-05-15 |
| **Status** | ✓ Active & Approved |

**Secrets Management:** All API keys, database credentials, LLM API keys stored in GitHub Secrets (encrypted). Never committed to repository.

---

### 10. [FUTURE] Anthropic (LLM / Fine-tuning) ⏳ Evaluating

| Field | Value |
|-------|-------|
| **Vendor** | Anthropic |
| **Service** | Claude API, Fine-tuning (under evaluation) |
| **Data Shared** | Conversation data (with explicit user consent) |
| **Purpose** | Model fine-tuning for improved accuracy |
| **Data Retention** | [TBD] |
| **Deletion Capability** | [TBD] |
| **Encryption In-Transit** | [TBD] |
| **Encryption At-Rest** | [TBD] |
| **SOC 2 Certification** | [TBD] |
| **DPA Status** | **Pending** (vendor under evaluation) |
| **Sub-processors** | [TBD] |
| **Audit Access** | [TBD] |
| **Security Certifications** | [TBD] |
| **Incident Notification** | [TBD] |
| **Data Location** | [TBD] |
| **Risk Level** | [TBD] |
| **Status** | ⏳ **Under Evaluation** (security assessment in progress) |

**Next Steps:**
- [ ] Request Anthropic security questionnaire
- [ ] Request SOC 2 Type II report (or equivalent)
- [ ] Negotiate DPA with Anthropic legal
- [ ] Finalize data retention and deletion terms
- [ ] Complete vendor security assessment
- [ ] Approval decision (timeline: 2026-05-01)

---

## DPA Tracking Checklist

| Vendor | DPA Signed | Date Signed | Renewal Date | Renewal Due | Status |
|--------|-----------|------------|---|---|---|
| OpenAI | ✓ | 2026-01-15 | 2027-01-15 | 9 months | ✓ Active |
| Twilio | ✓ | 2025-11-20 | 2026-11-20 | 7 months | ✓ Active |
| Stripe | ✓ | 2025-10-30 | 2026-10-30 | 6 months | ✓ Active |
| AWS | ✓ | 2025-09-01 | 2026-09-01 | 5 months | ✓ Active |
| Google Analytics | ✓ | 2026-02-10 | 2027-02-10 | 10 months | ✓ Active |
| Auth0 | ⏳ Pending | — | — | — | ⚠ In Progress (due 2026-05-01) |
| SendGrid | ✓ | 2025-12-05 | 2026-12-05 | 8 months | ✓ Active |
| Datadog | ✓ | 2026-03-01 | 2027-03-01 | 11 months | ✓ Active |
| GitHub | ✓ | 2025-08-15 | 2026-08-15 | 4 months | ✓ Active |
| Anthropic | ⏳ Pending | — | — | — | ⏳ Evaluating (decision due 2026-05-01) |

---

## Vendor Review Schedule

### Quarterly Review Process (<!-- CUSTOMIZE: adjust schedule -->)

**Next Review Dates:**
- Q2 2026 (Apr–Jun): OpenAI, AWS, Datadog
- Q3 2026 (Jul–Sep): Twilio, Auth0, GitHub
- Q4 2026 (Oct–Dec): Stripe, SendGrid, Google Analytics
- Q1 2027: Anthropic (if approved)

**Review Checklist for Each Vendor:**
- [ ] Check vendor security status page for incidents
- [ ] Review latest security/compliance reports
- [ ] Verify DPA is still active and terms acceptable
- [ ] Confirm no data breaches reported
- [ ] Confirm vendor still meets SOC 2 or equivalent
- [ ] Review pricing/contract terms
- [ ] Update risk assessment if needed
- [ ] Document review in this table (update "Last Reviewed" date)

---

## Incident Response: Vendor Breach

If a vendor reports a breach or security incident:

1. **Immediate (within 1 hour):**
   - [ ] Assess: Does the incident affect customer data?
   - [ ] Determine affected data types (PII, payment data, conversation history, etc.)
   - [ ] Determine incident timeline (when was data compromised?)
   - [ ] Check vendor DPA for notification obligations

2. **Assessment (within 4 hours):**
   - [ ] Review vendor's incident report
   - [ ] Assess customer impact (what data was exposed?)
   - [ ] Determine if breach notification required (GDPR 72-hour rule, CCPA, state laws)
   - [ ] Consult legal/privacy team

3. **Response (within 24 hours):**
   - [ ] Notify customers if required (email + public statement)
   - [ ] Update security disclosure page (SECURITY-PAGE-TEMPLATE.md)
   - [ ] Document incident in risk register
   - [ ] Consider vendor replacement if critical risk

4. **Follow-up:**
   - [ ] Root cause analysis from vendor
   - [ ] Verify corrective actions
   - [ ] Require vendor security certification/SOC 2 update
   - [ ] Update risk assessment for vendor

**Vendor Incident Contact Email:** Keep emergency contact for each vendor (usually security@vendor.com or similar).

---

## New Vendor Onboarding

Before integrating a new vendor, follow this checklist:

- [ ] **VENDOR-ASSESSMENT.md:** Complete security questionnaire
- [ ] **SOC 2 Report:** Request SOC 2 Type II report (or equivalent ISO 27001)
- [ ] **DPA:** Negotiate Data Processing Agreement
- [ ] **Risk Assessment:** Evaluate risk level (low/medium/high)
- [ ] **Data Minimization:** Ensure only essential data is shared
- [ ] **Retention Policy:** Confirm vendor's data retention terms
- [ ] **Deletion Capability:** Verify vendor can delete data on request
- [ ] **Incident Notification:** Confirm vendor will notify on breach
- [ ] **Legal Review:** Have legal team review DPA
- [ ] **Executive Approval:** CEO/Founder approval before integration
- [ ] **Documentation:** Update this table
- [ ] **Customer Notification:** Update Privacy Policy and security disclosures
- [ ] **Integration Testing:** Test data flows and deletion procedures
- [ ] **Monitoring:** Configure alerts for vendor incidents/status page

---

## Vendor Alternative / Contingency Planning

Identify alternatives for critical vendors:

| Primary Vendor | Service Category | Alternative Vendor 1 | Alternative Vendor 2 | Notes |
|---|---|---|---|---|
| OpenAI | LLM | Anthropic Claude | Google Vertex AI | Anthropic under evaluation; Google not yet integrated |
| Twilio | Voice/SMS | Vonage (Nexmo) | Bandwidth | Vonage is SOC 2 Type II certified |
| Stripe | Payment | Braintree / PayPal | Square | All three are SOC 2 Type II and PCI DSS L1 |
| AWS | Infrastructure | Google Cloud Platform | Microsoft Azure | Both are SOC 2 Type II; would require significant refactoring |
| Datadog | Monitoring | New Relic | Prometheus + Grafana | New Relic is SaaS managed; Prometheus requires self-hosting |

---

## Customer Notification

Customers have the right to know which vendors process their data (GDPR Article 28).

**Disclosure Location:**
- Privacy Policy: List all subprocessors
- Security Page (SECURITY-PAGE-TEMPLATE.md): Summary table of vendors
- Data Processing Agreement (if requested by customer)

**Sample Privacy Policy Language:**
> "We use third-party service providers to process your data. These vendors include: OpenAI (for AI responses), Stripe (for payments), AWS (for hosting), and others listed in our [Subprocessor Inventory](https://[YOUR DOMAIN]/subprocessors). All vendors have signed Data Processing Agreements and maintain SOC 2 certification."

---

## Change Log

| Date | Change | Owner |
|------|--------|-------|
| [DATE] | Initial inventory | [YOUR NAME] |
| [DATE] | Added Auth0 and Anthropic evaluation | [YOUR NAME] |

---

## Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Compliance Lead | [YOUR NAME] | _____________ | ________ |
| CEO / Founder | [YOUR NAME] | _____________ | ________ |
