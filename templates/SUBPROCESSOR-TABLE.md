# Subprocessor / Vendor Inventory

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME], Compliance Lead

---

## Team Size Adaptation

This template uses role names like "Compliance Lead" as a placeholder. For solo founders, you fill all these roles yourself. Use your own name. For small teams (2–5), assign roles based on who handles vendor relationships. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This document maintains an inventory of all third-party vendors and subprocessors that handle customer data on behalf of [YOUR COMPANY]. Each vendor is assessed for security posture, independent attestations, and data handling practices.

Two GDPR duties make this list public-facing. When you act as a processor for business customers, Article 28(2) requires their written authorisation before you engage another processor, and under a general authorisation you must tell them about any added or replaced subprocessor so they can object. When you are the controller (a consumer app), Article 13(1)(e) requires your privacy notice to name the recipients or categories of recipients of personal data.

<!-- CUSTOMIZE: Replace the example vendors with your own. The example values were read from each vendor's own pages on 2026-09-30; vendors change retention, training and residency terms often, so confirm every cell before you rely on it. Cells marked [CHECK] are ones the vendor's public pages did not settle. -->

---

## Subprocessor Inventory

Training and retention are separate columns because they are separate defaults: a vendor can promise never to train on your data and still keep every request for weeks.

| Vendor Name | Service Category | Data Shared | Purpose | Vendor Retention Default | Training Default | Zero Data Retention | SOC 2 Report | DPA Signed | Risk Level | Last Reviewed | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **OpenAI** | LLM API | Conversation text, hashed user ID | Generate AI responses | Up to 30 days (abuse monitoring) | Not used unless you opt in | By OpenAI approval | Type 2 | [DATE] | Medium | [DATE] | ✓ Active |
| **Deepgram** | Speech to text | User audio | Transcribe speech | Kept for model improvement unless opted out | Yes, opt-out per request | Per request (`mip_opt_out=true`) | Type 2 | [DATE] | High | [DATE] | ✓ Active |
| **ElevenLabs** | Text to speech | Response text, generated audio | Character voice | History kept by default; deleted data in backups up to 30 days | Yes, opt-out in account settings | Zero Retention Mode, Enterprise plan | Type 2 | [DATE] | High | [DATE] | ✓ Active |
| **LiveKit Cloud** | Real-time media | Live audio and video; transcripts and traces if observability is on | Run real-time sessions | Agent observability 30 days, when enabled | Inference data not used | Inference: by default | Type II | [DATE] | High | [DATE] | ✓ Active |
| **Tavus** | Avatar video | Response audio driving the avatar; recordings if enabled | Video avatar | Recordings off unless enabled, delivered to your own bucket | Not used (pricing page) | Enterprise plan | On Enterprise plan | [DATE] | Medium | [DATE] | ⏳ Evaluating |
| **Pinecone** | Vector store | Embeddings and their metadata | Retrieval for AI responses | [CHECK] | [CHECK] | [CHECK] | Yes | [DATE] | Medium | [DATE] | ✓ Active |
| **Twilio** | Voice / SMS API | Phone numbers, voice recordings, transcripts | Voice interaction, SMS delivery | Recordings kept until you delete them | [CHECK] | [CHECK] | Yes | [DATE] | Medium | [DATE] | ✓ Active |
| **Stripe** | Payment Processor | Card last-4, billing name/address, email | Process payments | No fixed period: kept while Stripe provides the service, then for its legal, regulatory, fraud-prevention, tax and accounting obligations | [CHECK] | n/a | Type II | [DATE] | High | [DATE] | ✓ Active |
| **AWS** | Cloud Infrastructure | All application data, backups, logs | Hosting, storage, compute | Set by you | n/a | n/a | Yes | [DATE] | High | [DATE] | ✓ Active |
| **Google Analytics** | Analytics | Usage events, cookie and device identifiers, device type | Track feature usage | 2 months (settable to 14) | n/a | n/a | [CHECK] | [DATE] | Low | [DATE] | ✓ Active |
| **Auth0** | Authentication | Email, password hash, MFA factors | User authentication | [CHECK] | n/a | n/a | Yes | Pending | Medium | [DATE] | ⚠ Pending DPA |
| **SendGrid** | Email Service | Email addresses, user ID | Transactional email | Event history 30 days | [CHECK] | n/a | Yes | [DATE] | Low | [DATE] | ✓ Active |
| **Datadog** | Monitoring / Logging | Application logs, performance metrics, user IDs (pseudonymized) | System monitoring, alerting | Set by your plan | n/a | n/a | Type 2 | [DATE] | Medium | [DATE] | ✓ Active |
| **GitHub** | Code Repository | Source code, contributor emails | Version control | Until repository deletion | n/a | n/a | Type 2 | [DATE] | High | [DATE] | ✓ Active |
| **[FUTURE] Anthropic** | LLM API | Conversation text, hashed user ID | Alternative LLM provider | Up to 30 days; flagged content up to 2 years | Not used | By arrangement with Anthropic | Type 2 | Pending | Medium | [DATE] | ⏳ Evaluating |

---

## Vendor Details & Risk Assessment

### 1. OpenAI (LLM)

| Field | Value |
|-------|-------|
| **Vendor** | OpenAI |
| **Service** | LLM API ([MODEL IDS YOU CALL]; record the exact IDs, since OpenAI retires models on a published schedule) |
| **Data Shared** | User conversation text, metadata (user_id hashed, timestamps) |
| **Purpose** | Generate AI responses to user prompts |
| **API Endpoint** | [ENDPOINTS YOU CALL] (zero data retention covers some endpoints and not others) |
| **Data Retention** | Abuse monitoring logs, which can hold prompts and responses, kept up to 30 days to enforce usage policies, longer only where law requires it or to protect against harm. Conversations stored through the conversations API keep that data until deleted |
| **Training Default** | Not used to train or improve OpenAI models unless you explicitly opt in |
| **Zero Data Retention** | Available subject to OpenAI's prior approval, requested through sales. Endpoints not eligible for ZDR (among them conversations, agents, assistants, threads, vector stores, files, fine-tuning jobs and batches) may still store application state |
| **Deletion Capability** | Abuse monitoring logs expire after up to 30 days; files you upload (for example for fine-tuning) stay until you delete them |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, OpenAI infrastructure |
| **SOC 2 Report** | Type 2 (period: [DATES OF THE REPORT YOU OBTAINED]) |
| **DPA Status** | Signed [DATE] |
| **Sub-processors** | Published list at openai.com/policies/sub-processor-list, including several cloud infrastructure providers |
| **Audit Access** | SOC reports and certificates through OpenAI's trust portal |
| **Security Certifications** | For the API Platform, per OpenAI's product compliance status page: SOC 2 Type 2, ISO/IEC 27001 (covering 27017 and 27018 controls) and ISO/IEC 27701. The trust portal lists more without naming product scope. HIPAA BAA on request |
| **Incident Notification** | Per DPA: without undue delay after becoming aware of a personal data breach (no hour count) |
| **Data Location** | US by default; other regions by approval |
| **Risk Level** | **Medium** (largest recipient of conversation data) |
| **Mitigations** | • Send only the conversation text the response needs<br/>• Use hashed user IDs only<br/>• Request zero data retention if your data is sensitive<br/>• Monitor OpenAI status page for incidents<br/>• Regular vendor security reviews<br/>• Alternative LLM vendors identified for contingency |
| **Last Security Review** | [DATE] (quarterly review) |
| **Next Review** | [DATE + 3 MONTHS] |
| **Status** | ✓ Active & Approved |

**Training Data Usage:** OpenAI does not use API data to train or improve its models unless the customer opts in. Confirm at each review that no one on your account has opted in.

---

### 2. Twilio (Voice / SMS)

| Field | Value |
|-------|-------|
| **Vendor** | Twilio Inc. |
| **Service** | Voice API, SMS API, Programmable Voice |
| **Data Shared** | Phone numbers, voice recordings (audio files), transcriptions |
| **Purpose** | Enable voice calls and SMS interactions in [YOUR APP] |
| **Data Retention** | Twilio keeps recordings until you delete them. [YOUR COMPANY] deletes recordings after [7] days through the API. Recording metadata stays 40 days after deletion. Call logs: [CHECK] |
| **Deletion Capability** | Delete through the REST API or Console; deletion is final. A recording status callback can trigger download and deletion automatically |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Twilio infrastructure |
| **SOC 2 Report** | Yes (period: [DATES]) |
| **DPA Status** | Signed [DATE] |
| **Sub-processors** | Published on Twilio's sub-processor page |
| **Audit Access** | Reports through the Twilio Trust Center |
| **Security Certifications** | SOC 2, ISO/IEC 27001, 27017, 27018, PCI DSS, HIPAA |
| **Incident Notification** | Per DPA: without undue delay after discovery of a security incident (no hour count) |
| **Data Location** | US1 by default; IE1 (Ireland) and AU1 (Australia) Regions available. Twilio does not guarantee all data stays in the selected Region, and not every product runs outside US1 |
| **Risk Level** | **Medium** (voice and audio data is sensitive) |
| **Mitigations** | • Delete recordings after [7] days through the API<br/>• Monitor Twilio incidents and security advisories<br/>• Review retention logs monthly<br/>• User consent obtained before voice recording |
| **Last Security Review** | [DATE] (quarterly review) |
| **Next Review** | [DATE + 3 MONTHS] |
| **Status** | ✓ Active & Approved |

**Data Deletion Verification:** Monthly task to confirm the deletion job ran and no recording older than [7] days remains.

---

### 3. Stripe (Payment)

| Field | Value |
|-------|-------|
| **Vendor** | Stripe Inc. |
| **Service** | Payment Processing, Billing |
| **Data Shared** | Card last-4 digits, billing name, address, email, payment amount, transaction ID |
| **Purpose** | Process customer payments, generate invoices |
| **Data Retention** | Stripe states no fixed period: data is kept while Stripe provides the service and longer where needed for legal and regulatory obligations, fraud prevention, and tax, accounting and financial reporting. Any multi-year retention of transaction records comes from tax and financial law in your jurisdictions; PCI DSS sets no such period |
| **Deletion Capability** | Customer can request card deletion; Stripe retains transaction records for its legal obligations |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, tokenization (card data never stored in [YOUR DATABASE]) |
| **PCI DSS Compliance** | PCI DSS Service Provider Level 1 |
| **SOC 2 Report** | Type II, issued yearly, on request (period: [DATES]) |
| **DPA Status** | Signed [DATE] |
| **Sub-processors** | Published on Stripe's sub-processor page |
| **Audit Access** | SOC 1 and SOC 2 reports on request; SOC 3 public |
| **Security Certifications** | PCI DSS Service Provider Level 1, SOC 1, SOC 2 Type II, SOC 3 |
| **Incident Notification** | Per DPA: without undue delay, and no later than 48 hours for incidents affecting personal data under the GDPR or UK GDPR |
| **Data Location** | [CHECK] |
| **Risk Level** | **High** (payment data = financial/identity risk) |
| **Mitigations** | • Use Stripe tokenization (never store full card numbers)<br/>• Webhook signature validation for all Stripe events<br/>• Monitor Stripe security advisories<br/>• Validate PCI DSS compliance once a year: Self-Assessment Questionnaire A for Stripe Checkout or Elements, or a Report on Compliance at merchant Level 1<br/>• Incident response plan for payment processor breach<br/>• 3-D Secure enabled for high-risk transactions |
| **Last Security Review** | [DATE] (quarterly review) |
| **Next Review** | [DATE + 3 MONTHS] |
| **Status** | ✓ Active & Approved |

**PCI Compliance:** Stripe Checkout and Elements collect card details in fields Stripe hosts, so card numbers never reach your servers. That narrows your PCI DSS scope without removing it. Your merchant level follows your own annual card transaction volume; Stripe's Level 1 is Stripe's own rating as a service provider. At Levels 2 to 4 you validate once a year with Self-Assessment Questionnaire A, signed by a Qualified Security Assessor or Internal Security Assessor at Level 2. A Level 1 merchant cannot use a questionnaire and files a Report on Compliance instead.

---

### 4. AWS (Infrastructure)

| Field | Value |
|-------|-------|
| **Vendor** | Amazon Web Services, Inc. |
| **Service** | EC2, RDS, S3, CloudWatch, IAM, VPC |
| **Data Shared** | **ALL** application data (database, backups, logs, configuration) |
| **Purpose** | Cloud hosting, storage, compute, disaster recovery |
| **Data Retention** | Per [YOUR COMPANY] retention policy (see DATA-RETENTION-POLICY.md) |
| **Deletion Capability** | Yes, AWS provides deletion APIs |
| **Encryption In-Transit** | Yes, TLS 1.2+, VPN/VPC isolation |
| **Encryption At-Rest** | Yes, AES-256 (KMS managed keys) |
| **SOC 2 Report** | Yes, through AWS Artifact (period: [DATES]) |
| **DPA Status** | Signed [DATE] (AWS Data Processing Addendum, part of the AWS Service Terms) |
| **Sub-processors** | Published on AWS's sub-processor page |
| **Audit Access** | AWS Artifact for SOC reports and certificates |
| **Security Certifications** | SOC 1, SOC 2, SOC 3, ISO 27001, 27017, 27018, 27701, 42001, PCI DSS, HIPAA, FedRAMP |
| **Incident Notification** | Per DPA: without undue delay after becoming aware of a security incident (no hour count). Security Bulletins carry wider advisories |
| **Data Location** | [YOUR REGION] (<!-- CUSTOMIZE: e.g., us-east-1 -->). Per the AWS DPA, AWS does not move customer data out of the regions you select except as needed to provide the service or to comply with law |
| **Risk Level** | **High** (hosts all data) |
| **Mitigations** | • AWS Config rules for compliance monitoring<br/>• VPC security groups and NACLs<br/>• IAM least-privilege policies<br/>• KMS encryption for sensitive data<br/>• Automated backups and cross-region replication<br/>• AWS Security Hub monitoring<br/>• Quarterly AWS security assessment<br/>• Incident response runbook for AWS breach |
| **Last Security Review** | [DATE] (quarterly review) |
| **Next Review** | [DATE + 3 MONTHS] |
| **Status** | ✓ Active & Approved |

**Multi-AZ & Disaster Recovery:** Production infrastructure spans 2 AZs; automatic failover configured.

---

### 5. Google Analytics

| Field | Value |
|-------|-------|
| **Vendor** | Google LLC |
| **Service** | Google Analytics 4 (GA4) |
| **Data Shared** | Page views, clicks, device type, referrer, IP address, and cookie and device identifiers. GA4 uses IP addresses for coarse location (and outside the EU, Switzerland and the UK for spam detection), then discards them; it does not log or store them. In a property linked to Google Ads, encrypted IP addresses can flow to the Ads account |
| **Purpose** | Track feature usage, understand user behavior, product analytics |
| **Data Retention** | User-level and event-level data: 2 months by default, settable to 14 months (GA4 360 offers longer for event data). Aggregated standard reports are not affected |
| **Deletion Capability** | Per-user deletion through the Google Analytics Admin API; data also expires on the retention setting |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Google infrastructure |
| **SOC 2 Report** | [CHECK] |
| **DPA Status** | Google Ads Data Processing Terms accepted [DATE] (they list Google Analytics as a processor service) |
| **Sub-processors** | Published by Google for its ads and analytics processor services |
| **Audit Access** | Limited; Google provides privacy control documentation |
| **Security Certifications** | ISO 27001 (committed in the Ads Data Processing Terms) |
| **Incident Notification** | Per the Ads Data Processing Terms: promptly and without undue delay |
| **Data Location** | [CHECK] |
| **Risk Level** | **Low** (usage data with pseudonymous identifiers; no account data sent) |
| **Mitigations** | • Exclude internal traffic from analytics<br/>• Set retention to the shortest period your reports need<br/>• Check whether the property is linked to Google Ads, since a link changes where IP-derived data can flow<br/>• Disclose GA4 in the privacy policy and gate it on consent where required<br/>• Monitor Google privacy documentation for changes |
| **Last Security Review** | [DATE] (quarterly review) |
| **Next Review** | [DATE + 3 MONTHS] |
| **Status** | ✓ Active & Approved |

**GDPR:** GA4 processes personal data (Google lists cookie identifiers, IP addresses, device identifiers and client identifiers), so it needs a lawful basis, a privacy notice entry, and in the EU and UK usually consent for the analytics cookies.

---

### 6. Auth0 (Authentication) ⚠ Pending DPA

| Field | Value |
|-------|-------|
| **Vendor** | Auth0, Inc. (owned by Okta) |
| **Service** | Authentication (OAuth 2.0, SAML, passwordless) |
| **Data Shared** | Email address, password hash (Auth0-managed), MFA factors, last login date |
| **Purpose** | User authentication, identity management, MFA |
| **Data Retention** | Until user account deletion; Okta's own retention terms: [CHECK] |
| **Deletion Capability** | Auth0 provides account deletion API |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Okta infrastructure |
| **SOC 2 Report** | Yes, through the Okta Security Trust Center (period: [DATES]) |
| **DPA Status** | **PENDING** (DPA draft received; review in progress) |
| **Sub-processors** | Published by Okta |
| **Audit Access** | Reports through the Okta Security Trust Center, on request |
| **Security Certifications** | Okta and Auth0: SOC 1, SOC 2, SOC 3, ISO/IEC 27001, 27017, 27018, PCI DSS, HIPAA, FedRAMP, CSA STAR. Check per-product scope in the reports |
| **Incident Notification** | Per Okta DPA: without undue delay after confirming a security breach (no hour count) |
| **Data Location** | Auth0 public cloud regions: US, EU, Australia, Canada, Japan, UK (chosen per tenant) |
| **Risk Level** | **Medium** (authentication = critical access control; DPA pending) |
| **Status** | ⚠ **Pending DPA Signature** (do not send customer data until DPA signed) |

**Action Items:**
- [ ] Negotiate DPA with Auth0 (due: [DATE])
- [ ] Sign DPA once approved
- [ ] Update this table with signed date
- [ ] Notify customers of the new subprocessor once the DPA is signed (see Customer Notification below)
- **Interim Mitigation:** Only enable Auth0 for internal testing; customers should use alternative auth method until DPA signed

---

### 7. SendGrid (Email)

| Field | Value |
|-------|-------|
| **Vendor** | Twilio SendGrid |
| **Service** | Transactional Email, Email Delivery |
| **Data Shared** | Customer email addresses, email content (transactional only), user ID |
| **Purpose** | Send transactional emails (password reset, receipts, alerts) |
| **Data Retention** | Email event history 30 days, not extendable. Suppression lists: [CHECK] |
| **Deletion Capability** | Manual suppression list management; per-recipient deletion through the API |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Twilio infrastructure |
| **SOC 2 Report** | Yes, through the Twilio Trust Center (period: [DATES]) |
| **DPA Status** | Signed [DATE] (the Twilio DPA covers SendGrid) |
| **Sub-processors** | Published on Twilio's sub-processor page |
| **Audit Access** | Reports through the Twilio Trust Center |
| **Security Certifications** | Twilio Trust Center: SOC 2, ISO/IEC 27001, 27017, 27018, PCI DSS, HIPAA. Check SendGrid's scope in the reports |
| **Incident Notification** | Per the Twilio DPA: without undue delay (no hour count). SendGrid backups are deleted one year after termination |
| **Data Location** | Global by default; EU residency through an EU subuser on the EU API host with an EU-provisioned dedicated IP (marketing, activity and validation features are unavailable to EU subusers) |
| **Risk Level** | **Low** (transactional email only; no customer data in body) |
| **Mitigations** | • Only send transactional emails (no customer data in body)<br/>• Comply with CAN-SPAM requirements<br/>• Monitor SendGrid bounce/complaint rates<br/>• Unsubscribe link in all emails<br/>• Monitor SendGrid status page for incidents |
| **Last Security Review** | [DATE] (quarterly review) |
| **Next Review** | [DATE + 3 MONTHS] |
| **Status** | ✓ Active & Approved |

---

### 8. Datadog (Monitoring)

| Field | Value |
|-------|-------|
| **Vendor** | Datadog, Inc. |
| **Service** | Application Performance Monitoring (APM), Log Management, Alerting |
| **Data Shared** | Application logs (may contain pseudonymized user IDs), performance metrics, error traces |
| **Purpose** | Monitor application health, incident detection, performance analysis |
| **Data Retention** | Set by your plan or contract: [YOUR INDEX RETENTION] (standard indexing is 15 days by default for on-demand customers, or 3, 7, 15 or 30 days by contract; Flex Logs up to 15 months); archives are self-hosted in your own storage |
| **Deletion Capability** | Automatic purge per retention setting; manual deletion available |
| **Encryption In-Transit** | Yes, TLS 1.2+ |
| **Encryption At-Rest** | Yes, Datadog infrastructure |
| **SOC 2 Report** | Type 2 (period: [DATES]) |
| **DPA Status** | Signed [DATE] |
| **Sub-processors** | Published by Datadog |
| **Audit Access** | Reports through the Datadog trust center |
| **Security Certifications** | SOC 2 Type 2, ISO/IEC 27001, 27017, 27018, 27701, 42001, PCI DSS, HIPAA, FedRAMP, CSA STAR |
| **Incident Notification** | Per DPA: without undue delay after becoming aware of a personal data breach (no hour count) |
| **Data Location** | The Datadog site you choose ([YOUR SITE], e.g. US1 or EU1); sites do not share data |
| **Risk Level** | **Medium** (logs can carry user identifiers) |
| **Mitigations** | • Pseudonymize user IDs in logs before sending to Datadog<br/>• Keep index retention at the shortest period you need<br/>• Review sampled logs for PII leakage quarterly<br/>• Monitor Datadog status page for incidents |
| **Last Security Review** | [DATE] (quarterly review) |
| **Next Review** | [DATE + 3 MONTHS] |
| **Status** | ✓ Active & Approved |

---

### 9. GitHub (Code Repository)

| Field | Value |
|-------|-------|
| **Vendor** | GitHub, Inc. (owned by Microsoft) |
| **Service** | Git Repository, CI/CD (GitHub Actions), Secrets Management |
| **Data Shared** | Source code, contributor emails, CI/CD secrets, deployment logs |
| **Purpose** | Version control, code collaboration, automated testing/deployment |
| **Data Retention** | Until you delete the repository (GitHub's docs state no retention period) |
| **Deletion Capability** | Repository deletion available. A force push hides commits but leaves them reachable in clones and forks, by SHA in cached views, and through pull requests that reference them. GitHub Support purges cached views only for sensitive data that rotating credentials cannot fix, so treat any secret that reached GitHub as exposed and rotate it |
| **Encryption In-Transit** | Yes, TLS 1.2+, SSH key support |
| **Encryption At-Rest** | Yes, GitHub/Microsoft infrastructure |
| **SOC 2 Report** | Type 2 (period: [DATES]) |
| **DPA Status** | Signed [DATE] (GitHub Data Protection Agreement) |
| **Sub-processors** | Published by GitHub |
| **Audit Access** | Compliance reports in organization settings (GitHub Enterprise Cloud) |
| **Security Certifications** | SOC 1 Type 2, SOC 2 Type 2, ISO/IEC 27001, CSA STAR Level 2, PCI DSS attestation |
| **Incident Notification** | Per DPA: without undue delay (no hour count) |
| **Data Location** | US by default; EU, Australia, US and Japan residency on GitHub Enterprise Cloud with data residency |
| **Risk Level** | **High** (source code is your IP, and a breached repository exposes it) |
| **Mitigations** | • Private repository (not public)<br/>• Branch protection rules (require code review)<br/>• Signed commits required<br/>• Secrets scanning and push protection enabled<br/>• Dependabot for vulnerability scanning<br/>• Regular audit of repository access permissions<br/>• No hardcoded secrets in git history (use GitHub Secrets for CI/CD)<br/>• Incident response plan for repository compromise |
| **Last Security Review** | [DATE] (quarterly review) |
| **Next Review** | [DATE + 3 MONTHS] |
| **Status** | ✓ Active & Approved |

**Secrets Management:** All API keys, database credentials, LLM API keys stored in GitHub Secrets (encrypted). Never committed to repository.

---

### 10. [FUTURE] Anthropic (LLM) ⏳ Evaluating

| Field | Value |
|-------|-------|
| **Vendor** | Anthropic |
| **Service** | Claude API ([MODEL IDS UNDER EVALUATION]). The Claude API offers no fine-tuning |
| **Data Shared** | Conversation text, hashed user ID |
| **Purpose** | Alternative LLM provider for AI responses |
| **Data Retention** | Anthropic's privacy center sets a ceiling: inputs and outputs deleted within 30 days. Its API documentation adds that conversation content is not retained by default. Content flagged by trust and safety kept up to 2 years and classifier scores up to 7 years. Some models require 30-day retention; check the API docs for the models you use |
| **Training Default** | Customer content from the API is not used to train models |
| **Zero Data Retention** | By arrangement through Anthropic sales, enabled per organization. Several features are excluded (batch processing, the Files API, code execution, the MCP connector and others); check the current list |
| **Deletion Capability** | Per DPA: customer data deleted within 30 days of termination, except where law requires otherwise |
| **Encryption In-Transit** | [CHECK] |
| **Encryption At-Rest** | [CHECK] |
| **SOC 2 Report** | Type 2, with a bridge letter (period: [DATES]) |
| **DPA Status** | **Pending** (vendor under evaluation) |
| **Sub-processors** | [CHECK] |
| **Audit Access** | Reports through Anthropic's trust center |
| **Security Certifications** | SOC 2 Type 2, ISO 27001, ISO/IEC 42001, CSA STAR, HIPAA (BAA available) |
| **Incident Notification** | Per DPA: without undue delay, and in any event within 48 hours |
| **Data Location** | Inference location set per request or workspace (global by default, or US); workspace setting governs storage at rest |
| **Risk Level** | [TBD after assessment] |
| **Status** | ⏳ **Under Evaluation** (security assessment in progress) |

**Next Steps:**
- [ ] Complete VENDOR-ASSESSMENT.md for Anthropic
- [ ] Obtain the SOC 2 Type 2 report and bridge letter
- [ ] Sign the DPA
- [ ] Decide whether to request zero data retention
- [ ] Approval decision (due: [DATE])

---

### 11. AI Pipeline Vendors: Speech, Voice, Real-Time Media, Avatar, Vector Store

An AI product's pipeline adds vendors a conventional SaaS stack does not have, and their defaults differ more than the LLM providers' do. The speech and voice vendors below train on customer content by default unless you opt out. Fill a full detail block like the ones above for each vendor you adopt; this table records the defaults that most often surprise people.

| Vendor | Default You Must Change | Breach Notice in DPA | Data Location | Certifications (vendor's trust page) |
|---|---|---|---|---|
| **Deepgram** (speech to text) | Requests join Deepgram's Model Improvement Program by default and audio and transcripts are kept to improve its models. Send `mip_opt_out=true` on every request to have data kept only as long as processing needs | [CHECK] | Global by default; EU and Australia endpoints. Fully in-region only for opted-out requests | SOC 2 Type 1 and Type 2, HIPAA, PCI |
| **ElevenLabs** (text to speech, voice agents) | Content licensed to improve the service by default; opt out under the account's data use settings. Zero Retention Mode is Enterprise only and excludes voice cloning, dubbing and music | Without undue delay upon confirming a security incident | US by default; EU, India and Singapore environments on Enterprise, with some support and moderation processing outside the region | SOC 2 Type 2, ISO/IEC 27001, 27701, 42001, PCI DSS, HIPAA |
| **LiveKit Cloud** (real-time media, agent inference) | Agent observability records audio, transcripts and traces for 30 days once enabled; turn it off per session (`record=False`) or for the project if you don't need it. LiveKit Inference is zero-retention by default | Without undue delay, and no later than 72 hours | US by default or EU (Frankfurt), fixed when the project is created; media pinning on Scale plan or higher | SOC 2 Type II, HIPAA (BAA available) |
| **Tavus** (avatar video) | Recording is off unless you enable it, and recordings go to your own storage bucket; zero data retention on the Enterprise plan | [CHECK] | [CHECK] | SOC 2 and HIPAA reports on the Enterprise plan |
| **Pinecone** (vector store) | [CHECK]: retention, training and deletion terms were not settled by its public pages | [CHECK] | US and customer-selected cloud regions | SOC 2, ISO/IEC 27001, HIPAA |

<!-- CUSTOMIZE: Voice cloning, custom voices and avatar likeness need the depicted person's consent on record; see VENDOR-ASSESSMENT.md 9.3.4. -->

---

## DPA Tracking Checklist

Breach notice windows differ, and most DPAs give no hour count at all. Your own notification clock (72 hours to a GDPR supervisory authority) starts when you become aware, which can be days after the vendor did.

| Vendor | DPA Signed | Date Signed | DPA Version Date | Breach Notice Window (per DPA) | Next Review | Status |
|--------|-----------|------------|---|---|---|---|
| OpenAI | ✓ | [DATE] | [VERSION DATE] | Without undue delay | [DATE + 12 MONTHS] | ✓ Active |
| Deepgram | ✓ | [DATE] | [VERSION DATE] | [CHECK] | [DATE + 12 MONTHS] | ✓ Active |
| ElevenLabs | ✓ | [DATE] | [VERSION DATE] | Without undue delay | [DATE + 12 MONTHS] | ✓ Active |
| LiveKit Cloud | ✓ | [DATE] | [VERSION DATE] | Without undue delay, max 72 hours | [DATE + 12 MONTHS] | ✓ Active |
| Twilio | ✓ | [DATE] | [VERSION DATE] | Without undue delay | [DATE + 12 MONTHS] | ✓ Active |
| Stripe | ✓ | [DATE] | [VERSION DATE] | Without undue delay; max 48 hours for GDPR/UK GDPR data | [DATE + 12 MONTHS] | ✓ Active |
| AWS | ✓ | [DATE] | [VERSION DATE] | Without undue delay | [DATE + 12 MONTHS] | ✓ Active |
| Google Analytics | ✓ | [DATE] | [VERSION DATE] | Promptly and without undue delay | [DATE + 12 MONTHS] | ✓ Active |
| Auth0 | ⏳ Pending | [DATE] | [VERSION DATE] | Without undue delay | [DATE] | ⚠ In Progress (due [DATE]) |
| SendGrid | ✓ | [DATE] | [VERSION DATE] | Without undue delay | [DATE + 12 MONTHS] | ✓ Active |
| Datadog | ✓ | [DATE] | [VERSION DATE] | Without undue delay | [DATE + 12 MONTHS] | ✓ Active |
| GitHub | ✓ | [DATE] | [VERSION DATE] | Without undue delay | [DATE + 12 MONTHS] | ✓ Active |
| Anthropic | ⏳ Pending | [DATE] | [VERSION DATE] | Without undue delay, max 48 hours | [DATE] | ⏳ Evaluating (decision due [DATE]) |

<!-- CUSTOMIZE: Vendors update DPAs on their own schedule. At each review, record the version date of the DPA in force and re-read the breach clause; a changed window changes your incident plan. -->

---

## Vendor Review Schedule

### Quarterly Review Process (<!-- CUSTOMIZE: adjust schedule -->)

**Rotation (each vendor reviewed at least once a year, highest risk first):**
- [QUARTER 1]: OpenAI, Deepgram, ElevenLabs, AWS
- [QUARTER 2]: LiveKit Cloud, Twilio, Auth0, GitHub
- [QUARTER 3]: Stripe, Datadog, Pinecone
- [QUARTER 4]: SendGrid, Google Analytics, any vendor added during the year

**Review Checklist for Each Vendor:**
- [ ] Check vendor security status page for incidents
- [ ] Obtain the latest SOC 2 report or bridge letter and check its period
- [ ] Verify DPA is still active and record its current version date
- [ ] Re-read retention, training and zero data retention terms; vendors change these
- [ ] Confirm no data breaches reported
- [ ] Review pricing/contract terms
- [ ] Update risk assessment if needed
- [ ] Document review in this table (update "Last Reviewed" date)

---

## Incident Response: Vendor Breach

If a vendor reports a breach or security incident:

1. **Immediate (within 1 hour):**
   - [ ] Assess: Does the incident affect customer data?
   - [ ] Determine affected data types (PII, payment data, conversation history, voice recordings, etc.)
   - [ ] Determine incident timeline (when was data compromised, and when did the vendor learn of it?)
   - [ ] Check vendor DPA for notification obligations

2. **Assessment (within 4 hours):**
   - [ ] Review vendor's incident report
   - [ ] Assess customer impact (what data was exposed?)
   - [ ] Determine whether breach notification is required (GDPR's 72 hours to the supervisory authority, state breach laws, notice owed to business customers under your own DPAs; see INCIDENT-RESPONSE-PLAN.md)
   - [ ] Consult legal/privacy advisor

3. **Response (within 24 hours):**
   - [ ] Notify customers if required (email + public statement)
   - [ ] Update security disclosure page (SECURITY-PAGE-TEMPLATE.md)
   - [ ] Document incident in risk register
   - [ ] Consider vendor replacement if critical risk

4. **Follow-up:**
   - [ ] Root cause analysis from vendor
   - [ ] Verify corrective actions
   - [ ] Obtain the vendor's next SOC 2 report or bridge letter and check whether it covers the fix
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
- [ ] **Retention and Training:** Record the vendor's retention default, its training default, and whether zero data retention is available and switched on
- [ ] **Deletion Capability:** Verify vendor can delete data on request
- [ ] **Incident Notification:** Record the DPA's breach notice window
- [ ] **Legal Review:** Have legal team review DPA
- [ ] **Executive Approval:** CEO/Founder approval before integration
- [ ] **Documentation:** Update this table
- [ ] **Customer Notification:** Update Privacy Policy and the published subprocessor list; give business customers the notice their DPA requires before the vendor goes live
- [ ] **Integration Testing:** Test data flows and deletion procedures
- [ ] **Monitoring:** Configure alerts for vendor incidents/status page

---

## Vendor Alternative / Contingency Planning

Identify alternatives for critical vendors:

| Primary Vendor | Service Category | Alternative Vendor 1 | Alternative Vendor 2 | Notes |
|---|---|---|---|---|
| OpenAI | LLM | Anthropic Claude | Google Gemini (paid tier or Google Cloud) | Anthropic under evaluation; Gemini's free tier trains on content, so only the paid tier qualifies |
| Deepgram | Speech to text | [ALTERNATIVE] | [ALTERNATIVE] | Check each alternative's training default |
| Twilio | Voice/SMS | Vonage (Nexmo) | Bandwidth | Check each alternative's trust center before relying on it |
| Stripe | Payment | Braintree / PayPal | Square | Check each alternative's trust center before relying on it |
| AWS | Infrastructure | Google Cloud Platform | Microsoft Azure | Would require significant refactoring |
| Datadog | Monitoring | New Relic | Prometheus + Grafana | New Relic is SaaS managed; Prometheus requires self-hosting |

---

## Customer Notification

Who you owe notice to depends on your role. Business customers who have you process their data authorise your subprocessors under GDPR Article 28(2), and under a general authorisation you must tell them before adding or replacing one so they can object. Consumers are owed the recipients or categories of recipients of their data in your privacy notice under Article 13(1)(e).

**Disclosure Location:**
- Privacy Policy: list subprocessors or their categories
- A published subprocessor list with a way for business customers to subscribe to changes
- Security Page (SECURITY-PAGE-TEMPLATE.md): summary table of vendors
- Data Processing Agreement with business customers: the authorisation and the notice period for changes

**Sample Privacy Policy Language:**
> "We use third-party service providers to process your data. These vendors include: [VENDOR] (for AI responses), [VENDOR] (for speech recognition), [VENDOR] (for payments), [VENDOR] (for hosting), and others listed in our [Subprocessor List](https://[YOUR DOMAIN]/subprocessors). Every vendor has signed a Data Processing Agreement, and each one's current security attestations are listed there."

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
