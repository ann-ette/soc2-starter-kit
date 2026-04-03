# SOC 2 Control Mapping

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME], Compliance Lead
**Assessment Type:** SOC 2 Type II (audited by independent third party annually)

---

## Team Size Adaptation

This template uses role names like "Compliance Lead" as a placeholder. For solo founders, you fill all these roles yourself — simply use your own name. For small teams (2–5), assign roles based on who oversees compliance. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This document maps [YOUR COMPANY]'s security controls to SOC 2 Trust Service Criteria (TSC). SOC 2 Type II compliance demonstrates to customers that we have implemented and maintained appropriate controls over information security, availability, processing integrity, confidentiality, and privacy.

**SOC 2 Criteria Categories:**
- **CC (Common Criteria):** 1–9 (organization and management controls)
- **A (Availability):** A1 (service availability control)
- **PI (Processing Integrity):** PI1 (system monitoring and completeness)
- **C (Confidentiality):** C1 (confidentiality control)
- **P (Privacy):** P1–P8 (privacy management)

<!-- CUSTOMIZE: Update control descriptions and evidence sources to match your infrastructure -->

---

## CC1: Organization and Governance

### CC1.1 — Entity Obtains or Generates, Uses, and Communicates Relevant, Quality Information Regarding the Objectives of Information and Related Responsibilities

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.1** | Board/Executive Oversight | Board minutes, security policy, CEO sign-off on policies | ✓ Implemented | 2026-03-01 |
| | Security Policy | SECURITY-POLICY.md (if exists) or Risk Register documented | ✓ Implemented | 2026-03-01 |
| | Roles & Responsibilities | Organization chart, RACI matrix, security team assignments | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Written security policy signed by executive leadership
- [ ] Clear assignment of security responsibilities
- [ ] Regular board/management communication on security
- [ ] Annual risk assessment and strategy documentation

---

### CC1.2 — The Board of Directors Demonstrates Independence from Management and Exercises Oversight

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.2** | Board/Management Separation | Board governance policy, meeting minutes | ✓ Implemented | 2026-03-01 |
| | Independent Review | Security audits, compliance assessments | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Board receives security compliance status reports quarterly
- [ ] Independent auditors assess security controls annually
- [ ] Management reports to board on incidents and remediation

**Note:** For solo/early-stage companies, this may be self-reported or external auditor review only.

---

### CC1.3 — Management Establishes Structures, Reporting Lines, and Appropriate Authorities to Achieve Objectives

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.3** | Organizational Structure | Org chart, roles/responsibilities documented | ✓ Implemented | 2026-03-01 |
| | Security Leadership | Security Lead / CISO role defined, reporting to CEO | ✓ Implemented | 2026-03-01 |
| | Incident Escalation | Incident response plan with escalation procedures | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Clear organizational structure (team roles)
- [ ] Security team has direct line to CEO/CFO
- [ ] Incident response procedures documented with escalation

---

### CC1.4 — The Entity Demonstrates a Commitment to Competence and Enforces Accountability for Performance of Responsibilities

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.4** | Security Training | Annual security training records, attendance logs | ✓ Implemented | 2026-01-15 |
| | Competency Requirements | Job descriptions, security training requirements | ✓ Implemented | 2026-01-15 |
| | Performance Accountability | Performance reviews, incident post-mortems | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] All employees complete annual security awareness training
- [ ] Security team has relevant certifications (CISSP, CEH, etc.)
- [ ] Performance reviews include security responsibilities
- [ ] Incident post-mortems document accountability and lessons learned

---

### CC1.5 — The Entity Selects, Develops, and Performs Ongoing and Periodic Evaluations of Changes in the Business, Laws, Regulations, and Ecosystem to Inform the Risk Acceptances

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.5** | Regulatory Monitoring | Legal/compliance team tracks regulatory changes | ✓ Implemented | 2026-03-01 |
| | Risk Assessment | Quarterly risk reviews, risk register updates | ✓ Implemented | 2026-03-01 |
| | Business Change Review | Change management process for significant business changes | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Quarterly regulatory change review (GDPR, CCPA, state laws)
- [ ] Risk register updated quarterly
- [ ] New vendor/feature assessment process documented
- [ ] Customer contract review for security requirements

---

## CC2: Communication

### CC2.1 — The Entity Obtains or Generates, Uses, and Communicates Relevant, Quality Information Regarding Objectives and Responsibilities

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC2.1** | Security Policy Communication | Posted on intranet, annual training, employee handbook | ✓ Implemented | 2026-01-15 |
| | Roles Communication | Role assignments documented, shared with team | ✓ Implemented | 2026-01-15 |

**Evidence:**
- [ ] Security policy accessible to all employees
- [ ] Role assignments documented and communicated
- [ ] Changes to policies communicated promptly

---

### CC2.2 — The Entity Makes Available or Obtains Relevant, Quality Information to Support the Functioning of Internal Controls

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC2.2** | Incident Reporting | Internal incident reporting procedures, Slack/email channels | ✓ Implemented | 2026-03-01 |
| | Security Alerts | Monitoring alerts, vendor security bulletins forwarded | ✓ Implemented | 2026-03-01 |
| | Control Effectiveness Reports | Audit reports, vulnerability scan results | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Security team reviews vendor security advisories weekly
- [ ] Internal incident reporting system (GitHub issues, tickets)
- [ ] Regular reports on audit findings and remediation

---

## CC3: Risk Assessment

### CC3.1 — The Entity Specifies Objectives with Sufficient Clarity to Enable the Assessment of Risks Relating to Those Objectives

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC3.1** | Business Objectives | Business plan, customer commitments (SLA) | ✓ Implemented | 2026-03-01 |
| | Security Objectives | Security policy, control documentation | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Documented business objectives (revenue, availability, etc.)
- [ ] Security objectives aligned with business needs
- [ ] SLA commitments communicated to customers

---

### CC3.2 — The Entity Identifies Risks Across the Organization Relating to Achievement of the Specified Objectives

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC3.2** | Risk Identification | Risk Register (RISK-REGISTER.md), quarterly reviews | ✓ Implemented | 2026-03-15 |
| | Threat Assessment | Vulnerability scans, penetration tests, threat modeling | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Risk register maintained with 15+ risks identified
- [ ] Quarterly risk assessment updates
- [ ] Annual penetration test or vulnerability assessment
- [ ] Threat landscape review (e.g., OWASP Top 10)

---

### CC3.3 — The Entity Considers Potential for Fraud in Assessing Risks to Achievement of Objectives

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC3.3** | Fraud Risk Assessment | Risk register fraud section, payment processor reviews | ✓ Implemented | 2026-03-15 |
| | Fraud Controls | Payment verification, refund policies, abuse monitoring | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Fraud risk identified in risk register
- [ ] Fraud controls documented (payment verification, limits)
- [ ] Chargeback monitoring and response procedures

---

### CC3.4 — The Entity Identifies and Assesses Changes that Could Significantly Impact the System of Internal Controls

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC3.4** | Change Impact Assessment | CHANGE-MANAGEMENT-POLICY.md, change request template | ✓ Implemented | 2026-03-01 |
| | Risk Assessment for Changes | Risk scoring for significant changes, approval workflow | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] All significant changes reviewed for security/compliance impact
- [ ] Change management policy implemented
- [ ] Change documentation and approval records

---

## CC4: Monitoring Activities

### CC4.1 — The Entity Selects, Develops, and Performs Ongoing and Periodic Evaluations of the Effectiveness of Monitoring Tools

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC4.1** | Monitoring Tools | Datadog, AWS CloudWatch, security scanning tools | ✓ Implemented | 2026-03-01 |
| | Tool Effectiveness Review | Monitoring dashboard review, alert accuracy | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Monitoring tools configured and active
- [ ] Regular review of alert accuracy (false positives)
- [ ] Tool update and maintenance schedule

---

### CC4.2 — The Entity Monitors System Components and the Operation of Those Components for Anomalies

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC4.2** | Anomaly Detection | Real-time alerting, log analysis, dashboards | ✓ Implemented | 2026-03-01 |
| | Security Metrics | Error rates, latency, failed logins, API abuse | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Real-time alerting for anomalies (Datadog, PagerDuty)
- [ ] Security metrics tracked and dashboarded
- [ ] Regular review of anomalies detected and response

---

## CC5: Control Activities

### CC5.1 — The Entity Selects and Develops Control Activities that Contribute to the Mitigation of Risks

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC5.1** | Risk Mitigation Controls | Each risk in register has documented mitigations | ✓ Implemented | 2026-03-15 |
| | Control Design | Control documentation, evidence of implementation | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Each risk in risk register has documented mitigations
- [ ] Controls designed to address identified risks
- [ ] Regular testing of control effectiveness

---

### CC5.2 — The Entity Also Selects and Develops General Control Activities over Technology

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC5.2** | IT General Controls | Access controls, change management, backups | ✓ Implemented | 2026-03-01 |
| | Technology Security | Encryption, patch management, vulnerability scanning | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Encryption at rest (AES-256) and in transit (TLS 1.2+)
- [ ] Change management policy implemented
- [ ] Patch management and vulnerability scanning schedule
- [ ] Access controls (IAM, role-based access)
- [ ] Automated backups with testing

---

### CC5.3 — The Entity Deploys Control Activities through Policies and Procedures

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC5.3** | Policy Documentation | All control policies documented (this spreadsheet, linked docs) | ✓ Implemented | 2026-03-01 |
| | Procedure Implementation | Procedures are followed in practice (audit evidence) | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] All policies documented and accessible
- [ ] Procedures reflected in actual practice (code, logs)
- [ ] Regular audit of procedure compliance

---

## CC6: Logical and Physical Access Controls

### CC6.1 — The Entity Restricts Physical Access to Assets and Complementary Information Assets by Enforcing Logical Access Controls

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.1** | Logical Access Control | IAM policies, VPC security groups, database access controls | ✓ Implemented | 2026-03-01 |
| | MFA Enforcement | MFA required for admin/sensitive access | ✓ Implemented | 2026-03-01 |
| | Access Revocation | Offboarding checklist, access removal procedures | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] IAM least-privilege policies in place
- [ ] MFA required for all admin/sensitive accounts
- [ ] VPC security groups restrict access
- [ ] Database access controls documented
- [ ] Offboarding checklist with access revocation

---

### CC6.2 — Prior to Issuing System Credentials, the Entity Registers and Authorizes New Internal and External Users

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.2** | User Registration Process | Onboarding procedure, employee forms | ✓ Implemented | 2026-03-01 |
| | Authorization Process | Manager approval, role assignment | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Formal user registration process documented
- [ ] Manager approval required for access
- [ ] Role assignment based on job function
- [ ] Onboarding checklist

---

## CC7: Change Management

### CC7.1 — The Entity Authorizes, Designs, Builds, Configures, Documents, Tests, Approves, and Deploys Changes

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC7.1** | Change Management Policy | CHANGE-MANAGEMENT-POLICY.md, change request template | ✓ Implemented | 2026-03-01 |
| | Change Approval | Change request signs-off, PR reviews | ✓ Implemented | 2026-03-01 |
| | Testing & Validation | Test results in change request, staging deployment | ✓ Implemented | 2026-03-01 |
| | Deployment Documentation | Deployment logs, CHANGELOG.md, git commit history | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] All changes documented in change requests
- [ ] Approval process followed (code review, peer review)
- [ ] Testing evidence (unit tests, integration tests, staging)
- [ ] Deployment records (git logs, deployment dates)
- [ ] Rollback procedures tested

---

### CC7.2 — The Entity Authorizes, Designs, Builds, Configures, Documents, Tests, Approves, and Deploys Infrastructure Changes

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC7.2** | Infrastructure Change Process | AWS/Cloud change management, Terraform/IaC reviews | ✓ Implemented | 2026-03-01 |
| | Configuration Audits | AWS Config, periodic infrastructure audits | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Infrastructure as Code (IaC) with change control
- [ ] AWS Config monitoring for unauthorized changes
- [ ] Infrastructure changes reviewed and approved
- [ ] Configuration baseline documented

---

## CC8: Deficiency Management

### CC8.1 — The Entity Identifies, Records, and Resolves Exceptions to Objectives and Other Identified Deficiencies

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC8.1** | Deficiency Tracking | GitHub issues, security backlog, remediation log | ✓ Implemented | 2026-03-01 |
| | Remediation Tracking | Remediation due dates, completion verification | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Audit findings logged and tracked
- [ ] Remediation timelines assigned (critical: 7 days, high: 30 days)
- [ ] Remediation completion verified and documented
- [ ] Recurring issues analyzed for root cause

---

## CC9: Risk and Control Design and Implementation

### CC9.1 — The Entity Identifies, Selects, and Develops Risk Mitigation Activities for Risks Arising from Potential Business Disruptions

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC9.1** | Business Continuity | Disaster recovery plan, backup schedule, RTO/RPO | ✓ Implemented | 2026-03-01 |
| | Incident Response | Incident response plan, on-call procedures | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Disaster recovery plan documented with RTO/RPO
- [ ] Regular backup testing (quarterly)
- [ ] Incident response plan with contact procedures
- [ ] Post-incident reviews documented

---

## A1: Availability and Resilience

### A1.1 — The Entity Maintains, Monitors, and Evaluates the Current State of System Components and Holocomponents

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **A1.1** | Infrastructure Monitoring | Datadog, AWS CloudWatch, uptime monitoring | ✓ Implemented | 2026-03-01 |
| | Health Checks | Application health endpoints, database checks | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Uptime monitoring with 24/7 alerting
- [ ] Performance metrics (latency, throughput, errors)
- [ ] Database and application health checks
- [ ] Regular review of availability metrics

---

### A1.2 — The Entity Identifies, Develops, and Implements Recovery Strategies

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **A1.2** | Disaster Recovery Plan | DR plan document, RTO/RPO defined | ✓ Implemented | 2026-03-01 |
| | Recovery Procedures | Runbooks for common failures, failover procedures | ✓ Implemented | 2026-03-01 |
| | Testing | Quarterly DR drills, recovery time validation | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Documented DR plan with clear procedures
- [ ] Failover to secondary region/data center tested
- [ ] Recovery runbooks for critical services
- [ ] Quarterly DR drill with time verification

---

## PI1: System Monitoring and Completeness

### PI1.1 — The Entity Obtains or Generates, Uses, and Communicates Relevant, Quality Information Regarding Objectives of System Monitoring

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **PI1.1** | Data Completeness Monitoring | Transaction logging, data validation rules | ✓ Implemented | 2026-03-01 |
| | Monitoring Objectives | Monitoring policy, dashboard definitions | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Transaction logging enabled for all data modifications
- [ ] Data validation rules in application and database
- [ ] Monitoring dashboards track data completeness
- [ ] Regular reports on data quality

---

### PI1.2 — The Entity Monitors System Components and the Operations of Systems Monitoring for Anomalies

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **PI1.2** | Anomaly Detection | Real-time monitoring, duplicate/missing data alerts | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Alerts for data inconsistencies
- [ ] Duplicate record detection
- [ ] Missing required fields detection
- [ ] Regular reconciliation of data sources

---

## C1: Confidentiality

### C1.1 — The Entity Restricts Access to Information Assets and Use of Those Assets

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **C1.1** | Encryption at Rest | AES-256 encryption in database and backups | ✓ Implemented | 2026-03-01 |
| | Encryption in Transit | TLS 1.2+ for all API/database communications | ✓ Implemented | 2026-03-01 |
| | Key Management | KMS for key storage, key rotation schedule | ✓ Implemented | 2026-03-01 |
| | Access Controls | IAM policies, database user restrictions | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Encryption policy documented
- [ ] TLS certificates valid and auto-renewed
- [ ] Key rotation schedule followed
- [ ] Key access restricted to authorized services
- [ ] Access logs reviewed monthly

---

### C1.2 — The Entity Disposes of Information to Meet the Objectives Defined in the Entity's Information and System-Related Objectives

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **C1.2** | Data Retention Policy | DATA-RETENTION-POLICY.md, deletion procedures | ✓ Implemented | 2026-03-01 |
| | Secure Deletion | Encrypted deletion, verification procedures | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Data retention policy for each data type
- [ ] Automated deletion processes
- [ ] Deletion verification (query to confirm deletion)
- [ ] Backup data also deleted per retention schedule

---

## P1–P8: Privacy

### P1: Data Collection and Consent

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **P1** | Privacy Policy | Privacy policy posted, covers all data types | ✓ Implemented | 2026-03-01 |
| | Consent Mechanism | Consent forms, checkboxes for marketing/analytics | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Privacy policy updated and accessible
- [ ] Consent forms for marketing communications
- [ ] Analytics opt-out mechanism
- [ ] Cookie consent banner

---

### P2: Choice and Consent

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **P2** | Consent Management | User preferences, opt-out options | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Users can opt-out of marketing
- [ ] Users can manage data collection preferences
- [ ] Consent preferences stored and honored

---

### P3: Use, Retention, and Disposal

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **P3** | Data Usage Disclosure | Privacy policy details data usage | ✓ Implemented | 2026-03-01 |
| | Data Retention Policy | DATA-RETENTION-POLICY.md | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Privacy policy explains how data is used
- [ ] Retention periods disclosed
- [ ] Deletion procedures documented

---

### P4: Accuracy, Completeness, and Relevance

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **P4** | Data Accuracy | User ability to update profile, periodic audits | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Users can view and correct their data
- [ ] Data validation rules in forms
- [ ] Periodic data quality audits

---

### P5: Access, Amendment, and Portability

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **P5** | Data Subject Rights | DSAR process, data export, deletion capability | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Data Subject Access Request (DSAR) procedure documented
- [ ] Data export functionality (CSV/JSON)
- [ ] Deletion request handling process
- [ ] 30-day DSAR response SLA

---

### P6: Identification and Prevention of Unauthorized Access

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **P6** | Access Control | Authentication, authorization, encryption | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] User authentication required
- [ ] Role-based access to data
- [ ] Encryption of sensitive data
- [ ] Access logs reviewed

---

### P7: Accountability and Safeguards

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **P7** | Data Protection Program | Security policy, incident response, breach notification | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Security program documented
- [ ] Incident response plan
- [ ] Breach notification procedures (72-hour GDPR requirement)
- [ ] Third-party vendor DPAs

---

### P8: Quality and Reconstitution

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **P8** | Data Backup | Automated backups, encryption, tested recovery | ✓ Implemented | 2026-03-01 |

**Evidence:**
- [ ] Automated backup schedule
- [ ] Backup encryption
- [ ] Quarterly recovery testing
- [ ] Backup retention policy

---

## Control Effectiveness Assessment

### Testing & Validation

For each control implemented, evidence must demonstrate:

1. **Existence** — Control is documented and in place
2. **Execution** — Control is actually being performed
3. **Effectiveness** — Control is achieving its objective

| Control | Evidence of Existence | Evidence of Execution | Evidence of Effectiveness | Last Tested |
|---------|---|---|---|---|
| Access Control (CC6.1) | IAM policy document | Access logs, monthly review | No unauthorized access detected | 2026-03-01 |
| Encryption (C1.1) | Encryption policy | TLS certs, database encryption | Zero data breaches | 2026-03-01 |
| Change Management (CC7.1) | Change policy, template | Change requests, approvals | Zero unauthorized changes | 2026-03-01 |
| Backup & Recovery (A1.2) | DR plan, RTO/RPO | Backup logs, quarterly DR drill | Successful recovery in [X] hours | 2026-03-01 |

---

## SOC 2 Audit Readiness Checklist

**Before engaging an external auditor:**

- [ ] All controls documented and implemented
- [ ] Evidence gathered for 6+ months of operation
- [ ] Key control testing completed (access reviews, change logs, monitoring)
- [ ] All significant deficiencies remediated
- [ ] Incident response procedures tested
- [ ] Disaster recovery plan tested
- [ ] Vendor compliance verified (DPAs signed)
- [ ] Privacy policy and data handling documented
- [ ] Organization structure and responsibilities clear
- [ ] Training and competency records maintained

---

## Audit Scope & Timeline

| Item | Details |
|------|---------|
| Audit Type | SOC 2 Type II |
| Audit Scope | Cloud application [YOUR APP], infrastructure in [YOUR CLOUD PROVIDER] |
| Audit Period | [DATE] to [DATE] (typically 6–12 months) |
| Trust Service Criteria | CC1–CC9, A1, PI1, C1, P1–P8 |
| Auditor | [AUDIT FIRM NAME] |
| Audit Start Date | [DATE] |
| Expected Report Date | [DATE] |

---

## Annual SOC 2 Maintenance

After initial SOC 2 Type II audit:

- [ ] **Quarterly:** Internal control assessment
- [ ] **Semi-Annually:** Remediation of any audit findings
- [ ] **Annually:** External audit renewal

| Frequency | Task | Owner | Next Date |
|-----------|------|-------|-----------|
| Quarterly | Control effectiveness review | Security Lead | [DATE] |
| Quarterly | Risk register update | Compliance Lead | [DATE] |
| Semi-Annual | Audit finding remediation verification | All Leads | [DATE] |
| Annually | External SOC 2 audit | Third-party auditor | [DATE] |

---

## Document Control

| Version | Date | Change | Owner |
|---------|------|--------|-------|
| 1.0 | [DATE] | Initial SOC 2 control mapping | [YOUR NAME] |
| | | | |

---

## Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Security Lead | [YOUR NAME] | _____________ | ________ |
| Compliance Lead | [YOUR NAME] | _____________ | ________ |
| CEO / Founder | [YOUR NAME] | _____________ | ________ |
