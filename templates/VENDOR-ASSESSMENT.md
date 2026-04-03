# Vendor Security Assessment Questionnaire

**Company:** [YOUR COMPANY]
**Evaluating Vendor:** [VENDOR NAME]
**Assessment Date:** [DATE]
**Assessor:** [YOUR NAME], Security Lead
**Vendor Contact:** [VENDOR CONTACT NAME] ([VENDOR EMAIL])

---

## Team Size Adaptation

This template uses role names like "Security Lead" as a placeholder. For solo founders, you fill all these roles yourself — simply use your own name. For small teams (2–5), assign roles based on who evaluates vendors. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This questionnaire evaluates the security posture and compliance standards of prospective vendors before integrating them with [YOUR APP]. All vendors must meet minimum security requirements and provide evidence of compliance.

<!-- CUSTOMIZE: Customize severity levels and required scores based on your risk tolerance -->

---

## Assessment Scoring

| Rating | Definition | Threshold |
|--------|-----------|-----------|
| **Critical (C)** | Required for integration; any "No" fails assessment | Must be "Yes" |
| **High (H)** | Strongly preferred; "No" requires exception approval | Min 80% "Yes" |
| **Medium (M)** | Preferred; acceptable if vendor commits to remediate | Min 60% "Yes" |
| **Low (L)** | Nice-to-have; does not affect approval decision | No minimum |

**Overall Score:** (Approved if all Critical answers = "Yes" AND overall score ≥ 75%)

---

## Part 1: Company & Organizational Security

### 1.1 General Company Information

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 1.1.1 | What is the vendor's primary business and years in operation? | L | [ ] Yes | Business registration, website, LinkedIn | _____ |
| 1.1.2 | Does the vendor have a documented security program / Chief Information Security Officer (CISO)? | M | [ ] Yes | CISO contact, security policy link | _____ |
| 1.1.3 | Is the vendor financially stable? (Check credit rating, funding, major customers) | L | [ ] Yes | Dun & Bradstreet, Crunchbase, annual report | _____ |
| 1.1.4 | Has the vendor had any public security breaches in the past 3 years? | C | [ ] No | Security breach database search, vendor statement | _____ |
| 1.1.5 | Does the vendor have cyber liability insurance? | M | [ ] Yes | Certificate of Insurance, policy limits | _____ |

---

### 1.2 Certifications & Compliance

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 1.2.1 | Does the vendor maintain SOC 2 Type II certification? | C | [ ] Yes | SOC 2 report (audit within 1 year) | _____ |
| 1.2.2 | Does the vendor maintain ISO 27001 certification? | H | [ ] Yes | ISO 27001 certificate | _____ |
| 1.2.3 | Is the vendor PCI DSS compliant (if handling payment data)? | C | [ ] N/A or Yes | PCI DSS certification, SAQ | _____ |
| 1.2.4 | Does the vendor maintain HIPAA compliance (if health-related)? | C (conditional) | [ ] N/A or Yes | HIPAA Business Associate Agreement (BAA) | _____ |
| 1.2.5 | Does the vendor comply with GDPR? | C | [ ] Yes | GDPR compliance statement, Data Processing Agreement available | _____ |
| 1.2.6 | Does the vendor comply with CCPA / other privacy laws? | H | [ ] Yes | Privacy policy review, compliance documentation | _____ |

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
| 2.1.3 | Does the vendor use customer data for training AI/ML models without consent? | C | [ ] No / [ ] Opt-in available | Privacy policy review, DPA terms | _____ |
| 2.1.4 | Does the vendor sell or share customer data with third parties? | C | [ ] No / [ ] Only for service delivery | Privacy policy, terms of service | _____ |
| 2.1.5 | Can we prevent our data from being used for vendor's own product improvement? | H | [ ] Yes | DPA clause, product configuration option | _____ |
| 2.1.6 | Does the vendor allow opt-out from analytics / telemetry? | M | [ ] Yes | Configuration documentation | _____ |

---

### 2.2 Data Retention & Deletion

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 2.2.1 | What is the default data retention period? | C | [Specify: ___ days/months] | Data retention policy link | _____ |
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
| 4.1.2 | How quickly will the vendor notify us of a security breach? (SLA) | C | [Specify: ___ hours] | DPA clause, incident response timeline | _____ |
| 4.1.3 | Will the vendor notify regulators on our behalf (GDPR, CCPA)? | M | [ ] Yes / [ ] We coordinate | DPA terms | _____ |
| 4.1.4 | Does the vendor provide incident forensics/post-mortem? | M | [ ] Yes | Incident response process | _____ |
| 4.1.5 | Is there a dedicated security contact for incidents? | H | [ ] Yes | Emergency contact information | _____ |

---

### 4.2 Breach History & Transparency

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 4.2.1 | Has the vendor disclosed any security breaches in the past 3 years? | C | [ ] No | Security disclosures, breach database | _____ |
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
| 7.1.1 | Can we specify where our data is stored (country/region)? | H | [ ] Yes | Data residency options | _____ |
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

| # | Question | Critical | Answer | Evidence | Notes |
|---|----------|----------|--------|----------|-------|
| 9.1.1 | Does the vendor use our data for training their AI models? | C | [ ] No / [ ] Only with explicit consent | Privacy policy, DPA, feature documentation | _____ |
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
| 9.3.1 | Is voice/biometric data encrypted end-to-end? | C | [ ] Yes / [ ] N/A | Encryption documentation | _____ |
| 9.3.2 | Is voice/biometric data used for training without consent? | C | [ ] No / [ ] N/A | Privacy policy, DPA | _____ |
| 9.3.3 | Can voice/biometric data be used to create deepfakes? | L | Vendor should have safeguards | Policy documentation | _____ |

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

**Total Score:** _____ % (Approved if ≥ 75% and all Critical = "Yes")

**Recommendation:**

- [ ] **APPROVED** — Vendor meets security standards; proceed with integration
- [ ] **APPROVED WITH CONDITIONS** — Minor gaps acceptable; require remediation plan within [X] months
- [ ] **PENDING** — Need additional information or clarification from vendor (see below)
- [ ] **REJECTED** — Vendor does not meet security standards; recommend alternative

---

### Critical Issues (If Any)

If any Critical questions are answered "No", integration cannot proceed. List issues below:

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

If the vendor is approved despite some "No" answers, document the business justification and risk acceptance:

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

- **Critical (C):** Must be "Yes" for integration approval
- **High (H):** Strongly preferred; affects overall score significantly
- **Medium (M):** Preferred; vendor should have or commit to implement
- **Low (L):** Nice-to-have; informational only

All assessments should be completed by Security Lead and reviewed by Engineering/Compliance before vendor integration.

For questions or clarification, contact [YOUR EMAIL].
