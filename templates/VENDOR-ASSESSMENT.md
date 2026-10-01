# Vendor Security Assessment Questionnaire

**Company:** [YOUR COMPANY]
**Evaluating Vendor:** [VENDOR NAME]
**Assessment Date:** [DATE]
**Assessor:** [YOUR NAME], Security Lead
**Vendor Contact:** [VENDOR CONTACT NAME] ([VENDOR EMAIL])

---

## Team Size Adaptation

This template uses role names like "Security Lead" as a placeholder. For solo founders, you fill all these roles yourself. Use your own name. For small teams (2–5), assign roles based on who evaluates vendors. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This questionnaire evaluates the security posture and compliance standards of prospective vendors before integrating them with [YOUR APP]. All vendors must meet minimum security requirements and provide evidence of compliance.

<!-- CUSTOMIZE: Customize severity levels and required scores based on your risk tolerance -->

---

## Assessment Scoring

The Answer column shows the expected answer for each question. For most questions that is "Yes"; for some (does the vendor train on your data, does it sell your data) the answer you want is "No". Score each question as met or not met against the expected answer.

| Rating | Definition | Threshold |
|--------|-----------|-----------|
| **Critical (C)** | Required for integration; any Critical question not met fails the assessment | All met |
| **High (H)** | Strongly preferred; a High question not met requires exception approval | Min 80% met |
| **Medium (M)** | Preferred; acceptable if vendor commits to remediate | Min 60% met |
| **Low (L)** | Nice-to-have or informational; does not affect approval decision | No minimum |

**Overall Score:** (Approved if every Critical question is met AND overall score ≥ 75%)

---

## Part 1: Company & Organizational Security

### 1.1 General Company Information

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 1.1.1 | What is the vendor's primary business and years in operation? | L | [ ] Yes | Business registration, website, LinkedIn | _____ |
| 1.1.2 | Does the vendor have a documented security program / Chief Information Security Officer (CISO)? | M | [ ] Yes | CISO contact, security policy link | _____ |
| 1.1.3 | Is the vendor financially stable? (Check credit rating, funding, major customers) | L | [ ] Yes | Dun & Bradstreet, Crunchbase, annual report | _____ |
| 1.1.4 | List any public security breaches at the vendor in the past 3 years. A breach alone does not fail the vendor; 4.2.1 asks how it was handled | L | [List, or "none found"] | Security breach database search, news search, vendor statement | _____ |
| 1.1.5 | Does the vendor have cyber liability insurance? | M | [ ] Yes | Certificate of Insurance, policy limits | _____ |

---

### 1.2 Certifications & Compliance

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 1.2.1 | Does the vendor have a current independent security attestation: a SOC 2 Type II report, an ISO 27001 certificate, or an equivalent? | H | [ ] Yes | SOC 2 report whose period ended within the last 12 months, or ISO 27001 certificate and its scope statement | _____ |
| 1.2.2 | Does the vendor maintain ISO 27001 certification? | H | [ ] Yes | ISO 27001 certificate | _____ |
| 1.2.3 | Is the vendor PCI DSS compliant (if handling payment data)? | C | [ ] N/A or Yes | PCI DSS certification, SAQ | _____ |
| 1.2.4 | Does the vendor maintain HIPAA compliance (if health-related)? | C (conditional) | [ ] N/A or Yes | HIPAA Business Associate Agreement (BAA) | _____ |
| 1.2.5 | Does the vendor comply with GDPR? | C | [ ] Yes | GDPR compliance statement, Data Processing Agreement available | _____ |
| 1.2.6 | Does the vendor comply with CCPA / other privacy laws? | H | [ ] Yes | Privacy policy review, compliance documentation | _____ |

<!-- CUSTOMIZE: SOC 2 Type II is High rather than Critical because many AI startups worth using hold a Type I, an ISO 27001 certificate, or neither yet. Raise it to Critical if your own customers require it of your subprocessors. -->

**Reading the SOC 2 report** (answer these when 1.2.1 is met by a SOC 2 report; a report you have not read proves little):

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 1.2.7 | Does the report's system description cover the product and region you actually use? | H | [ ] Yes | Section 3 (system description) of the report | _____ |
| 1.2.8 | What period does it cover, and if it ended more than 3 months ago, has the vendor provided a bridge letter for the gap? | H | [Specify period] / [ ] Bridge letter | Report period; bridge (gap) letter | _____ |
| 1.2.9 | Is the auditor's opinion unqualified (clean)? | H | [ ] Yes | Section 1 (auditor's opinion) | _____ |
| 1.2.10 | Did the auditor's tests find exceptions, and does management's response explain each one? | M | [ ] None / [ ] Explained | Section 4 (tests and results) | _____ |
| 1.2.11 | Which complementary user entity controls (CUECs) does the report expect you to operate? List them and map each into your own controls | H | [List] | CUEC section of the report | _____ |
| 1.2.12 | Which subservice organizations (for example, the vendor's cloud host) are carved out, and have you obtained their reports? | M | [List] / [ ] Reports obtained | Carve-out section; subservice reports | _____ |

---

### 1.3 Third-Party Audits

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 1.3.1 | Has the vendor completed a recent penetration test? | H | [ ] Yes | Pentest report (past 12 months), summary | _____ |
| 1.3.2 | Does the vendor conduct regular vulnerability assessments? | H | [ ] Yes | Vulnerability assessment schedule, process | _____ |
| 1.3.3 | Does the vendor publish security audit reports publicly? | M | [ ] Yes | Link to audit reports or security page | _____ |

---

## Part 2: Data Handling & Privacy

### 2.1 Data Collection & Usage

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 2.1.1 | What data types does the vendor collect/process? | C | [Specify] | Vendor documentation, API documentation | _____ |
| 2.1.2 | Does the vendor have a clear, accessible privacy policy? | C | [ ] Yes | Privacy policy link, URL | _____ |
| 2.1.3 | Is customer data used to train AI/ML models by default on our plan? (Met: No, or an opt-out you have turned on) | C | [ ] No / [ ] Yes, with opt-out (per request, account setting or contract) / [ ] Yes, no opt-out | Privacy policy review, DPA terms | _____ |
| 2.1.4 | Does the vendor sell or share customer data with third parties? | C | [ ] No / [ ] Only for service delivery | Privacy policy, terms of service | _____ |
| 2.1.5 | Can we prevent our data from being used for vendor's own product improvement? | H | [ ] Yes | DPA clause, product configuration option | _____ |
| 2.1.6 | Does the vendor allow opt-out from analytics / telemetry? | M | [ ] Yes | Configuration documentation | _____ |

---

### 2.2 Data Retention & Deletion

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 2.2.1 | What does the vendor retain by default, for how long, and why? | C | [Specify: ___ days/months] Purpose: [ ] Abuse monitoring / [ ] Model improvement / [ ] Feature state / [ ] Other | Data retention policy link | _____ |
| 2.2.2 | Can we request custom retention periods? | M | [ ] Yes | DPA terms, vendor confirmation | _____ |
| 2.2.3 | Can we request permanent deletion of customer data? | C | [ ] Yes | Deletion policy, confirmation timeline | _____ |
| 2.2.4 | What is the timeframe for data deletion after request? | C | [Specify: ___ days] | DPA, data deletion SLA | _____ |
| 2.2.5 | Does the vendor certify deletion (proof of deletion)? | H | [ ] Yes | Deletion confirmation process, documentation | _____ |
| 2.2.6 | Does the vendor retain data in backups? How long? | M | [Specify: ___ months] | Backup retention policy | _____ |

---

### 2.3 Data Encryption

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 2.3.1 | Is data encrypted in transit (TLS 1.2+)? | C | [ ] Yes | API documentation, SSL certificate check | _____ |
| 2.3.2 | Is data encrypted at rest? | C | [ ] Yes | Encryption method and algorithm | _____ |
| 2.3.3 | What encryption algorithm is used (AES-256, etc.)? | M | [Specify: _______] | Technical documentation | _____ |
| 2.3.4 | Does the vendor manage encryption keys, or can we provide our own? | H | [ ] Vendor-managed / [ ] Customer-managed / [ ] Both | KMS documentation | _____ |
| 2.3.5 | Are backups encrypted? | H | [ ] Yes | Backup encryption policy | _____ |

---

## Part 3: Access Control & Authentication

### 3.1 User Access Control

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 3.1.1 | Does the vendor require strong authentication (MFA/2FA)? | H | [ ] Yes | Authentication policy documentation | _____ |
| 3.1.2 | Can we enforce MFA for our account? | M | [ ] Yes | Configuration options | _____ |
| 3.1.3 | Does the vendor use Role-Based Access Control (RBAC)? | M | [ ] Yes | Access control documentation | _____ |
| 3.1.4 | Can we manage which team members have access to what data? | H | [ ] Yes | Permission management documentation | _____ |
| 3.1.5 | Are user actions logged and auditable? | H | [ ] Yes | Audit log availability, retention | _____ |
| 3.1.6 | Can we export audit logs for our own records? | M | [ ] Yes | API/export capability | _____ |

---

### 3.2 API & Authentication Security

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 3.2.1 | Does the API require authentication (not public access)? | C | [ ] Yes | API documentation | _____ |
| 3.2.2 | Are API keys rotatable and revocable? | H | [ ] Yes | Key management policy | _____ |
| 3.2.3 | Does the vendor support OAuth 2.0 / JWT authentication? | M | [ ] Yes / [ ] Other: _____ | API authentication methods | _____ |
| 3.2.4 | Does the vendor enforce rate limiting on APIs? | M | [ ] Yes | Rate limiting policy, DDoS protection | _____ |
| 3.2.5 | Does the vendor support IP whitelisting? | M | [ ] Yes | Network security documentation | _____ |

---

## Part 4: Incident Response & Breach Management

### 4.1 Security Incident Response

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 4.1.1 | Does the vendor have a documented Incident Response Plan? | C | [ ] Yes | Incident response plan (can be summary) | _____ |
| 4.1.2 | How quickly does the DPA require the vendor to notify us of a security breach? (Many DPAs give no hour count, only "without undue delay") | C | [ ] Hour cap: ___ hours (all personal data / GDPR data only) / [ ] "Without undue delay", no hour cap | DPA clause, incident response timeline | _____ |
| 4.1.3 | Will the vendor notify regulators on our behalf (GDPR, CCPA)? | M | [ ] Yes / [ ] We coordinate | DPA terms | _____ |
| 4.1.4 | Does the vendor provide incident forensics/post-mortem? | M | [ ] Yes | Incident response process | _____ |
| 4.1.5 | Is there a dedicated security contact for incidents? | H | [ ] Yes | Emergency contact information | _____ |

---

### 4.2 Breach History & Transparency

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 4.2.1 | For each breach found in 1.1.4: did the vendor notify affected customers promptly, and publish what was exposed, the root cause, and the fix? | H | [ ] Yes / [ ] N/A (no breach) | Security disclosures, post-incident reports, breach database | _____ |
| 4.2.2 | Does the vendor have a public security page or disclosure page? | M | [ ] Yes | Security.txt, security page URL | _____ |
| 4.2.3 | Does the vendor publish a responsible disclosure policy? | M | [ ] Yes | Responsible Disclosure / Bug Bounty link | _____ |

---

## Part 5: Infrastructure & Availability

### 5.1 Infrastructure & Hosting

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 5.1.1 | What cloud provider(s) does the vendor use? | C | [Specify: AWS, GCP, Azure, etc.] | Infrastructure documentation | _____ |
| 5.1.2 | What is the SLA uptime commitment? | H | [Specify: ___ % uptime] | Service Level Agreement | _____ |
| 5.1.3 | Where are customer data centers located? (country/region) | C | [Specify: _______] | Data residency documentation | _____ |
| 5.1.4 | Does the vendor provide multi-region failover? | M | [ ] Yes | Disaster recovery documentation | _____ |
| 5.1.5 | Does the vendor publish a public status page? | M | [ ] Yes | Status page URL | _____ |

---

### 5.2 Disaster Recovery & Backups

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 5.2.1 | Does the vendor maintain automated backups? | C | [ ] Yes | Backup policy, frequency | _____ |
| 5.2.2 | What is the Recovery Time Objective (RTO)? | H | [Specify: ___ hours/minutes] | Disaster recovery plan | _____ |
| 5.2.3 | What is the Recovery Point Objective (RPO)? | H | [Specify: ___ hours] | Backup frequency, documentation | _____ |
| 5.2.4 | Are backups tested and verified regularly? | M | [ ] Yes | Backup testing schedule | _____ |
| 5.2.5 | Are backups stored in a separate geographic location? | H | [ ] Yes | Multi-region backup policy | _____ |

---

## Part 6: Third-Party & Supply Chain Security

### 6.1 Sub-processors & Third Parties

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 6.1.1 | What third-party vendors does the vendor use? (sub-processors) | C | [List: _______] | Sub-processor list, DPA | _____ |
| 6.1.2 | Are all sub-processors SOC 2 compliant? | M | [ ] Yes / [ ] Most | Sub-processor documentation | _____ |
| 6.1.3 | Will the vendor notify us if sub-processors change? | C | [ ] Yes | DPA clause, sub-processor notification | _____ |
| 6.1.4 | Can we opt-out of specific sub-processors? | M | [ ] Yes / [ ] No, but can use alternative | DPA terms | _____ |

---

### 6.2 Software Supply Chain Security

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 6.2.1 | Does the vendor perform dependency vulnerability scanning? | M | [ ] Yes | Dependency scanning tools (Dependabot, Snyk) | _____ |
| 6.2.2 | Does the vendor conduct code reviews for all changes? | H | [ ] Yes | Code review process, SDLC documentation | _____ |
| 6.2.3 | Does the vendor sign code commits with GPG/digital signatures? | M | [ ] Yes | Commit signing policy | _____ |
| 6.2.4 | Does the vendor publish a Software Bill of Materials (SBOM)? | M | [ ] Yes | SBOM availability | _____ |

---

## Part 7: Data Residency & Privacy Regulations

### 7.1 Data Residency

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 7.1.1 | Can we pin both storage and processing (inference, support, moderation) to a country or region, and on which plan? | H | Storage: [ ] Yes / Processing: [ ] Yes / Plan: ___ | Data residency options | _____ |
| 7.1.2 | Does the vendor comply with European GDPR requirements? | C (if EU customers) | [ ] Yes | GDPR compliance documentation | _____ |
| 7.1.3 | Does the vendor comply with California CCPA requirements? | H (if CA customers) | [ ] Yes | CCPA compliance documentation | _____ |
| 7.1.4 | Is the vendor compliant with other regional data protection laws? | M | [ ] Yes | Regional compliance documentation | _____ |

---

### 7.2 Data Transfer & Cross-Border Transfers

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 7.2.1 | Are cross-border data transfers compliant with regulations? | C | [ ] Yes | Data transfer mechanisms (SCCs, BCRs, etc.) | _____ |
| 7.2.2 | Does the vendor support data localization requirements? | M | [ ] Yes | Data residency controls | _____ |

---

## Part 8: Vendor Contracts & Legal Terms

### 8.1 Data Processing Agreement (DPA)

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 8.1.1 | Does the vendor provide a Data Processing Agreement (DPA)? | C | [ ] Yes | DPA template available, URL | _____ |
| 8.1.2 | Is the DPA compliant with GDPR Article 28? | C | [ ] Yes | Legal review of DPA terms | _____ |
| 8.1.3 | Does the DPA include data subject rights (DSAR, deletion, etc.)? | C | [ ] Yes | DPA terms review | _____ |
| 8.1.4 | Can we negotiate DPA terms, or is it take-it-or-leave-it? | M | [ ] Negotiable | Vendor flexibility | _____ |

---

### 8.2 Service Level Agreement (SLA) & Liability

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 8.2.1 | Is there a Service Level Agreement (SLA) with defined uptime? | H | [ ] Yes | SLA documentation | _____ |
| 8.2.2 | What is the vendor's liability cap in the contract? | M | [Specify: $___ or % of fee] | Service agreement | _____ |
| 8.2.3 | Are there penalties for SLA breaches? | M | [ ] Yes | SLA penalty structure | _____ |

---

### 8.3 Termination & Data Return

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 8.3.1 | Can we terminate the contract with 30 days notice? | M | [ ] Yes | Contract terms, termination clause | _____ |
| 8.3.2 | Will the vendor return/delete all our data after termination? | C | [ ] Yes | Data return/deletion policy | _____ |
| 8.3.3 | What is the timeline for data return post-termination? | M | [Specify: ___ days] | Contract terms | _____ |

---

## Part 9: AI/ML-Specific Questions (If Applicable)

### 9.1 Training Data & Model Usage

Some AI vendors train on customer data by default and offer an opt-out, per request or as an account setting. For 9.1.1 and 9.3.2, the question is met when the vendor does not train on your data or when you have turned the opt-out on.

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 9.1.1 | Is our data used to train the vendor's AI models by default on our plan? | C | [ ] No / [ ] Yes, with opt-out (per request, account setting or contract) / [ ] Yes, no opt-out | Privacy policy, DPA, feature documentation | _____ |
| 9.1.2 | Can we opt-out of model training? | C (if model training offered) | [ ] Yes / [ ] Not applicable | Opt-out mechanism, configuration | _____ |
| 9.1.3 | Does the vendor allow users to exclude their data from model training? | M | [ ] Yes / [ ] N/A | User privacy controls | _____ |
| 9.1.4 | Are we able to verify what data was used for training? | M | [ ] Yes / [ ] N/A | Model transparency, documentation | _____ |

---

### 9.2 Model Security & Prompt Injection

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 9.2.1 | Does the vendor implement input validation against prompt injection? | H | [ ] Yes | Security controls documentation | _____ |
| 9.2.2 | Does the vendor monitor for adversarial/malicious prompts? | M | [ ] Yes | Security monitoring, incident response | _____ |
| 9.2.3 | Can the vendor model memorize and regurgitate training data? | L | [ ] No / [ ] Mitigated | Model architecture documentation, testing | _____ |

---

### 9.3 Biometric & Voice Data (If Applicable)

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 9.3.1 | Is voice/biometric data encrypted in transit and at rest, and which vendor systems and staff can access it in the clear while it is processed? (A vendor that transcribes or synthesizes your audio has to decrypt it, so end-to-end encryption is not available for these services) | C | [ ] Yes / [ ] N/A | Encryption documentation, access policy | _____ |
| 9.3.2 | Is voice or audio data retained for model training by default? | C | [ ] No / [ ] Yes, opt-out per request / [ ] Yes, opt-out by account setting / [ ] Yes, no opt-out / [ ] N/A | Privacy policy, DPA | _____ |
| 9.3.3 | Can voice/biometric data be used to create deepfakes? | L | Vendor should have safeguards | Policy documentation | _____ |
| 9.3.4 | For voice cloning or custom voices: does the vendor require, verify and record the consent of the person whose voice is cloned? | C (if voice cloning used) | [ ] Yes / [ ] N/A | Voice cloning policy, consent flow | _____ |

---

### 9.4 Retention, Human Review and Model Lifecycle

Training and retention are separate controls: a vendor can promise not to train on your data and still keep every prompt for weeks.

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 9.4.1 | Separately from training: how long does the vendor keep prompts, outputs, audio and uploaded files, and for what purpose (abuse monitoring, debugging, legal hold)? | C | [Specify: ___ days, purpose] | DPA, data usage documentation | _____ |
| 9.4.2 | Is zero data retention (or an equivalent) available, is it on by default for your account or granted on approval, and which endpoints or features are excluded? | H | [ ] Default / [ ] On approval / [ ] Not offered; excluded: ___ | ZDR documentation, written confirmation for your organization | _____ |
| 9.4.3 | Do vendor staff or contractors review your inputs or outputs (for abuse, safety or quality), and under what conditions? | H | [Specify] | Data usage policy, DPA | _____ |
| 9.4.4 | What duties does the vendor's usage policy pass to you (telling users they are talking to AI, age limits, prohibited uses, content you must filter)? List them; each becomes one of your controls | C | [List] | Usage policy, terms of service | _____ |
| 9.4.5 | How much notice does the vendor give before deprecating or retiring a model you depend on? | M | [Specify: ___ days] | Deprecation policy | _____ |
| 9.4.6 | In which regions does inference run, and can you pin it to one? | H | [Specify] | Data residency or inference region documentation | _____ |
| 9.4.7 | Does the vendor hold ISO/IEC 42001 certification for its AI management system? | M | [ ] Yes | Certificate and its scope | _____ |

---

## Part 10: Support & Documentation

### 10.1 Support & SLA

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 10.1.1 | What is the vendor's support response time? | M | [Specify: ___ hours] | Support SLA documentation | _____ |
| 10.1.2 | Is 24/7 support available? | M | [ ] Yes / [ ] Business hours | Support contact page | _____ |
| 10.1.3 | Is there a dedicated security point of contact? | H | [ ] Yes | Contact information provided | _____ |

---

### 10.2 Documentation

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 10.2.1 | Is API documentation complete and up-to-date? | H | [ ] Yes | API docs link, quality review | _____ |
| 10.2.2 | Does the vendor provide security best practices documentation? | M | [ ] Yes | Security guides, samples | _____ |

---

## Summary & Recommendation

### Assessment Results

| Category | Critical Issues | High Issues | Medium Issues | Score | Status |
|----------|---|---|---|---|---|
| Organizational Security | [ ] | [ ] | [ ] | __% | ✓/⚠/✗ |
| Data Handling & Privacy | [ ] | [ ] | [ ] | __% | ✓/⚠/✗ |
| Access Control | [ ] | [ ] | [ ] | __% | ✓/⚠/✗ |
| Incident Response | [ ] | [ ] | [ ] | __% | ✓/⚠/✗ |
| Infrastructure | [ ] | [ ] | [ ] | __% | ✓/⚠/✗ |
| Supply Chain | [ ] | [ ] | [ ] | __% | ✓/⚠/✗ |
| Compliance & Legal | [ ] | [ ] | [ ] | __% | ✓/⚠/✗ |
| AI/ML-Specific | [ ] | [ ] | [ ] | __% | ✓/⚠/✗ |

---

### Overall Assessment Score

**Total Score:** _____ % (Approved if ≥ 75% and every Critical question is met)

**Recommendation:**

- [ ] **APPROVED**: Vendor meets security standards; proceed with integration
- [ ] **APPROVED WITH CONDITIONS**: Minor gaps acceptable; require remediation plan within [X] months
- [ ] **PENDING**: Need additional information or clarification from vendor (see below)
- [ ] **REJECTED**: Vendor does not meet security standards; recommend alternative

---

### Critical Issues (If Any)

If any Critical question is not met, integration cannot proceed. List issues below:

1. _______________________________________________________________
2. _______________________________________________________________
3. _______________________________________________________________

---

### Required Remediation / Next Steps

| Issue | Remediation Required | Deadline | Owner | Status |
|-------|---|---|---|---|
| | | | | |
| | | | | |

---

### Exceptions (If Approved with Conditions)

If the vendor is approved despite some questions not met, document the business justification and risk acceptance:

**Risk Acceptance:**
> We accept the following risks because [explain business need/justification]:
> - [Risk 1]
> - [Risk 2]

**Compensating Controls:**
> We mitigate these risks through the following controls:
> - [Control 1]
> - [Control 2]

**Approval Authority:** [NAME, TITLE]
**Approval Date:** [DATE]

---

### Vendor Contact Information

| Role | Name | Email | Phone |
|------|------|-------|-------|
| Sales | | | |
| Security | | | |
| Support | | | |
| Legal/Compliance | | | |

---

## Approval & Sign-Off

| Role | Name | Signature | Date | Status |
|------|------|-----------|------|--------|
| Security Lead | [YOUR NAME] | _________ | __/__/__ | [ ] |
| Engineering Lead | [YOUR NAME] | _________ | __/__/__ | [ ] |
| CEO / Founder | [YOUR NAME] | _________ | __/__/__ | [ ] |

---

## Follow-Up & Re-Assessment Schedule

- **First Assessment:** [DATE]
- **Next Review:** [DATE] (annually or per change)
- **Re-Assessment Triggers:** Major security incident, certification expired, significant business model change

---

## Document Version & History

| Version | Date | Change | Owner |
|---------|------|--------|-------|
| 1.0 | [DATE] | Initial assessment | [YOUR NAME] |
| | | | |

---

## Appendix: Assessment Template Notes

- **Critical (C):** Must meet the expected answer for integration approval
- **High (H):** Strongly preferred; affects overall score significantly
- **Medium (M):** Preferred; vendor should have or commit to implement
- **Low (L):** Nice-to-have; informational only

All assessments should be completed by Security Lead and reviewed by Engineering/Compliance before vendor integration.

For questions or clarification, contact [YOUR EMAIL].
