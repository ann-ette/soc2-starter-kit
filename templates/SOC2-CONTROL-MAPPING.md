# SOC 2 Control Mapping

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME], Compliance Lead
**Report Type Targeted:** [SOC 2 Type I / SOC 2 Type II]
**Categories in Scope:** Security (CC1 to CC9) [+ Availability] [+ Confidentiality] [+ Processing Integrity] [+ Privacy]

---

## Team Size Adaptation

This template uses role names like "Compliance Lead" as a placeholder. For solo founders, you fill all these roles yourself, so use your own name. For small teams (2 to 5), assign roles based on who oversees compliance. The controls are the same regardless of team size; only the assignment changes. Where a criterion assumes a second person (an independent board, segregation of duties), this file says so and names the compensating control a solo founder can show instead.

---

## Overview

This document maps [YOUR COMPANY]'s controls to the AICPA Trust Services Criteria (TSP Section 100, the 2017 criteria with the revised points of focus issued in 2022). Every criterion in the Security category appears below with its official number, in the order the AICPA publishes them, so an auditor can read this file against their own workpapers without translating.

**What the criteria numbers mean:**

| Group | Criteria | What it covers |
|---|---|---|
| CC1 | CC1.1 to CC1.5 | Control environment: integrity, oversight, structure, competence, accountability |
| CC2 | CC2.1 to CC2.3 | Communication and information, inside the company and with outside parties |
| CC3 | CC3.1 to CC3.4 | Risk assessment, including fraud and change |
| CC4 | CC4.1 to CC4.2 | Monitoring activities and deficiency handling |
| CC5 | CC5.1 to CC5.3 | Control activities, technology controls, policies |
| CC6 | CC6.1 to CC6.8 | Logical and physical access |
| CC7 | CC7.1 to CC7.5 | System operations: vulnerabilities, monitoring, incidents, recovery |
| CC8 | CC8.1 | Change management |
| CC9 | CC9.1 to CC9.2 | Risk mitigation: business disruption and vendors |
| A1 | A1.1 to A1.3 | Availability (optional category) |
| C1 | C1.1 to C1.2 | Confidentiality (optional category) |
| PI1 | PI1.1 to PI1.5 | Processing integrity (optional category) |
| P1 to P8 | P1.1 to P8.1 | Privacy (optional category, 18 criteria) |

The 33 common criteria (CC1 to CC9) make up the Security category, which every SOC 2 report includes. The other four categories are optional and add their own criteria on top.

**Choosing categories.** Most first reports for a small company cover Security alone, or Security plus Availability or Confidentiality, because those are what customers ask for. Privacy is the heaviest category and rarely the right first choice. Processing Integrity asks you to commit that processing is complete, valid and accurate, which is a hard commitment to make about generative output; most AI products leave it out. Delete the optional sections you are not putting in scope, and say in the header which ones remain.

<!-- CUSTOMIZE: Update control descriptions and evidence sources to match your infrastructure. The control names below are examples; your auditor tests what you actually do, so describe that. -->

---

## Status Legend

Every control row in this document ships as `☐ Not Started` with a `[DATE]` placeholder. That is the honest starting position for a template, and you move each row yourself as the control goes in.

| Status | Meaning |
|--------|---------|
| `☐ Not Started` | No control in place, or none you can evidence yet |
| `◐ In Progress` | Control partially in place, or evidence collection has begun |
| `✓ Implemented` | Control operating, with evidence an auditor could sample |
| `N/A` | Criterion does not apply to your system. Say why in the Evidence Source column |

**Last Verified** is the date you last looked at the control and confirmed it still operates. An empty or stale date on an `✓ Implemented` row is one of the first things an auditor asks about, so leave it as `[DATE]` until you have actually checked.

**One warning worth the sentence.** Marking a row `✓ Implemented` because you intend to implement it is the single easiest way to turn this document into a liability. A control mapping that overstates your position is worse than no control mapping, because you have now written the overstatement down.

---

## CC1: Control Environment

### CC1.1: Commitment to Integrity and Ethical Values

**Worked Example: How to Fill In a Control Row**

The three rows below are filled in to show the shape of a completed entry. Every other control row in this document is blank, and these three are the only exception. Reset them to `☐ Not Started` and `[DATE]` once you have read them, or overwrite them with your own position.

Read the Evidence Source column as the working part. "Code of conduct" is a weak entry because nobody can find it; "Code of conduct, `policies/` folder in the company drive, signed by every person with production access, re-signed each January" names an artifact an auditor can request. The date is illustrative, so replace it with the date you actually verified the control.

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.1** | Code of Conduct | Code of conduct, `policies/` folder, signed by the founder and each contractor, re-signed annually | ✓ Implemented | 2026-09-01 (example) |
| | Policy Acknowledgment | Dated acknowledgment of INFORMATION-SECURITY-POLICY.md by everyone with access to customer data | ✓ Implemented | 2026-09-01 (example) |
| | Contractor Agreements | Signed agreements carrying confidentiality and acceptable-use terms, `contracts/` folder | ◐ In Progress | 2026-09-01 (example) |

**Evidence:**
- [ ] Code of conduct, signed and dated
- [ ] Policy acknowledgments for everyone with access, including you
- [ ] Contractor agreements with confidentiality terms
- [ ] A written process for handling a violation, even a short one

---

### CC1.2: Board Independence and Oversight of Internal Control

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.2** | Oversight Body | Board, advisory board, or a documented statement that the company is founder-managed with no board | ☐ Not Started | [DATE] |
| | Independent Review | Periodic review of the security program by someone other than the founder (advisor, fractional security lead, readiness assessor) | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Minutes or notes from each oversight review, dated
- [ ] Security and incident status presented at each review
- [ ] Follow-up actions from the review tracked to closure

**Solo founder note.** A solo founder has no independent board, and an auditor will see that immediately. Say so in plain words and show the compensating control: an outside person who reviews the program on a schedule and whose notes you keep. Pretending a separation exists is worse than documenting that it does not.

---

### CC1.3: Structures, Reporting Lines, and Authorities

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.3** | Roles and Responsibilities | Role list or RACI, even if every row carries one name | ☐ Not Started | [DATE] |
| | Escalation Path | INCIDENT-RESPONSE-PLAN.md escalation section, including outside contacts | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Documented roles (security, privacy, engineering, vendor management)
- [ ] Escalation contacts for incidents, including vendors and any outside help

---

### CC1.4: Commitment to Competence

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.4** | Security Training | Annual security awareness training records, including the founder | ☐ Not Started | [DATE] |
| | Role Requirements | Written expectations for anyone given production access | ☐ Not Started | [DATE] |
| | Background Checks | Checks for people with production access, where lawful in their jurisdiction | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Training completion records with dates
- [ ] Onboarding checklist showing role requirements were met

---

### CC1.5: Accountability for Internal Control Responsibilities

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC1.5** | Accountability Terms | Security duties written into contractor agreements and role descriptions | ☐ Not Started | [DATE] |
| | Sanctions | Consequences for policy violations stated in INFORMATION-SECURITY-POLICY.md | ☐ Not Started | [DATE] |
| | Post-Incident Accountability | Post-incident reviews record what went wrong and who owns each fix | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Agreements or role descriptions naming security duties
- [ ] Post-incident reviews with named owners for follow-up actions

---

## CC2: Communication and Information

### CC2.1: Relevant, Quality Information Supports Internal Control

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC2.1** | System Inventory | ARCHITECTURE-MAP.md pages 1 and 5, reviewed quarterly | ☐ Not Started | [DATE] |
| | Data Flow Documentation | ARCHITECTURE-MAP.md pages 3, 4 and 6 | ☐ Not Started | [DATE] |
| | Control Inputs | Logs, scan results and reviews that feed the controls below (page 8) | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Architecture map with a current review date
- [ ] Inventory of systems, stores and vendors that matches SUBPROCESSOR-TABLE.md

---

### CC2.2: Internal Communication of Objectives and Responsibilities

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC2.2** | Policy Access | Policies stored where everyone with access can read them | ☐ Not Started | [DATE] |
| | Internal Reporting Channel | How anyone with access reports a security concern or incident | ☐ Not Started | [DATE] |
| | Change Communication | Policy changes announced and re-acknowledged | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Policy location documented
- [ ] Reporting channel documented in the incident response plan

---

### CC2.3: Communication with External Parties

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC2.3** | Customer Commitments | Terms of service, SLA if offered, and the security page (SECURITY-PAGE-TEMPLATE.md) | ☐ Not Started | [DATE] |
| | Vulnerability Reporting | Published reporting address and `/.well-known/security.txt` | ☐ Not Started | [DATE] |
| | Subprocessor Notices | Public subprocessor list and a way to notify customers of changes | ☐ Not Started | [DATE] |
| | AI Interaction Notice | In-product disclosure, at the point of interaction, that the user is talking to an AI system | ☐ Not Started | [DATE] |
| | Status and Incident Communication | Status page or equivalent; customer notification procedure | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Published security page and privacy policy, dated
- [ ] `security.txt` reachable at `/.well-known/security.txt`
- [ ] In-product AI disclosure captured as a dated screenshot
- [ ] Record of the last subprocessor change notice sent

---

## CC3: Risk Assessment

### CC3.1: Objectives Specified Clearly Enough to Assess Risk

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC3.1** | Service Commitments | Documented commitments to customers (security, availability, confidentiality) | ☐ Not Started | [DATE] |
| | System Requirements | The requirements your system must meet to keep those commitments | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Written list of service commitments and system requirements (your auditor will ask for these to build the system description)

---

### CC3.2: Risks Identified and Analyzed

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC3.2** | Risk Register | RISK-REGISTER.md, scored and reviewed quarterly | ☐ Not Started | [DATE] |
| | AI Threat Assessment | AI features assessed against the OWASP Top 10 for LLM Applications (2025), and agent features against the OWASP Top 10 for Agentic Applications (2026) | ☐ Not Started | [DATE] |
| | Technical Assessment | Vulnerability scans; penetration test when customers or risk call for one | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Risk register with likelihood, impact, owner and treatment for each risk
- [ ] Annual risk assessment, dated and signed
- [ ] AI-specific risks (prompt injection, unsafe output, cross-user leakage, cost abuse) assessed

---

### CC3.3: Potential for Fraud Considered

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC3.3** | Fraud Risk Assessment | Risk register entries for payment fraud, account takeover, API key theft and usage abuse | ☐ Not Started | [DATE] |
| | Fraud Controls | Payment verification, spend caps on AI providers, usage alerts, admin action logging | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Fraud risks in the register
- [ ] Provider spend limits and usage alerts configured (screenshot)
- [ ] Chargeback and abuse response procedure

---

### CC3.4: Changes That Could Affect Internal Control

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC3.4** | Regulatory Monitoring | Dated review of privacy, security and AI law changes in every market the product is available in | ☐ Not Started | [DATE] |
| | AI Transparency Assessment | Dated jurisdiction assessment for AI disclosure and output-marking duties, refreshed each review cycle | ☐ Not Started | [DATE] |
| | Business and Vendor Change Review | New features, vendors, models and markets reviewed for control impact before launch | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Quarterly regulatory change review, dated
- [ ] AI transparency assessment covering every jurisdiction the product is available in, dated and signed
- [ ] Machine-readable marking of generated output implemented and sampled, where required
- [ ] Risk register updated after each review, including RISK-016

<!-- CUSTOMIZE: AI transparency duties attach based on where your users are rather than where you are, so this assessment covers every market the product is available in. See SOC2-GUIDE.md, "Telling People They Are Talking to AI," for the current jurisdiction table and dates. -->

> **Scope note.** The Trust Services Criteria contain no AI-specific criterion. AI governance questions on a buyer questionnaire (AI policy with executive accountability, AI system inventory, per-system risk classification) fall outside SOC 2 and belong to ISO/IEC 42001. A SOC 2 report cannot answer them, and saying so plainly is a better answer than stretching a criterion to cover it. Some CPA firms will test ISO/IEC 42001 Annex A controls as additional subject matter in what they call a SOC 2+ report. You and the firm choose those criteria; the AICPA has published no AI criteria of its own. Its technical questions and answers on how a service organization's use of AI affects a SOC 2 examination (TQA section 9561, September 2026) are nonauthoritative guidance for auditors and add no criteria. See SOC2-GUIDE.md, "What ISO 42001 Covers That SOC 2 Does Not."

---

## CC4: Monitoring Activities

### CC4.1: Ongoing and Separate Evaluations of Controls

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC4.1** | Quarterly Control Self-Assessment | Walk this file each quarter and update every Last Verified date you actually checked | ☐ Not Started | [DATE] |
| | Separate Evaluation | Readiness assessment, penetration test, or outside review on a set cadence | ☐ Not Started | [DATE] |
| | Automated Checks | Scheduled scans whose results someone reads (CI security jobs, cloud configuration checks) | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Dated self-assessment records
- [ ] Reports from any separate evaluation

---

### CC4.2: Deficiencies Evaluated and Communicated

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC4.2** | Deficiency Tracking | Remediation tracker (COMPLIANCE-TRACKER-TEMPLATE.md, Sheet 1) | ☐ Not Started | [DATE] |
| | Remediation Deadlines | Severity-based targets (for example critical in 7 days, high in 30) and completion checks | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Findings logged with owner, target date and status
- [ ] Remediation verified and documented
- [ ] Recurring issues analyzed for root cause

---

## CC5: Control Activities

### CC5.1: Control Activities Selected to Mitigate Risk

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC5.1** | Risk to Control Mapping | Each risk in RISK-REGISTER.md names the controls that treat it | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Every high and critical risk has documented mitigations with evidence

---

### CC5.2: General Controls over Technology

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC5.2** | Technology Control Set | Access, change, backup, encryption and monitoring controls (CC6 to CC8) | ☐ Not Started | [DATE] |
| | Inherited Controls | Controls your hosting and AI providers operate, backed by their SOC 2 reports (see Complementary Controls below) | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] List of inherited controls and the vendor report that covers each

---

### CC5.3: Policies and Procedures

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC5.3** | Policy Set | INFORMATION-SECURITY-POLICY.md and the policies in this kit, versioned | ☐ Not Started | [DATE] |
| | Annual Review | Each policy reviewed and re-approved at least annually | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Policies with version history and approval dates
- [ ] Procedures reflected in actual practice (code, logs, records)

---

## CC6: Logical and Physical Access Controls

### CC6.1: Logical Access Security over Protected Assets

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.1** | Access Control | Least-privilege IAM roles, database access limited to service accounts | ☐ Not Started | [DATE] |
| | MFA Enforcement | MFA on cloud console, code host, domain registrar, email, and every AI and media provider console | ☐ Not Started | [DATE] |
| | Encryption at Rest | Database, object storage and backups encrypted | ☐ Not Started | [DATE] |
| | Asset Inventory | Systems and data stores listed in ARCHITECTURE-MAP.md | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] IAM policies or role list
- [ ] MFA settings screenshots for each console, dated
- [ ] Encryption settings for each store

---

### CC6.2: Registering, Authorizing and Removing Users

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.2** | Access Requests | Written approval before anyone gets access, including your own new accounts | ☐ Not Started | [DATE] |
| | Offboarding | Offboarding checklist that removes every account and rotates shared secrets | ☐ Not Started | [DATE] |
| | Service Accounts | Each service account and API key has a named owner and purpose | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Access request records
- [ ] Completed offboarding checklists
- [ ] Service account and key inventory (SECRETS-AUDIT-CHECKLIST.md)

---

### CC6.3: Role-Based Access, Least Privilege, and Segregation of Duties

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.3** | Access Reviews | Quarterly review of every account with production or customer-data access | ☐ Not Started | [DATE] |
| | Role Changes | Access adjusted when a role changes | ☐ Not Started | [DATE] |
| | Segregation of Duties | Who can change code, deploy, and read customer data; compensating controls where one person does all three | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Dated access review records, with what was removed
- [ ] Segregation of duties statement

**Solo founder note.** You hold every role, so segregation of duties does not exist in the usual sense. The compensating controls an auditor can test are mechanical: branch protection that requires CI to pass before merge, deploys only through the pipeline, audit logs you cannot edit, and a periodic review of those logs by someone outside the company. Write down which of these you run.

---

### CC6.4: Physical Access

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.4** | Data Center Access | Inherited from hosting provider; their SOC 2 report covers it | ☐ Not Started | [DATE] |
| | Workspace and Devices | Device lock, full-disk encryption, and where work devices are kept | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Hosting provider SOC 2 report on file, reviewed
- [ ] Device encryption and screen-lock settings, dated

---

### CC6.5: Disposal of Physical Assets

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.5** | Device Disposal | Laptops and drives wiped before reuse, sale or disposal, with a record | ☐ Not Started | [DATE] |
| | Media Disposal at Providers | Inherited from hosting provider | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Disposal or wipe records for retired devices

---

### CC6.6: Protection Against Threats from Outside the System Boundary

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.6** | Boundary Protection | TLS everywhere, firewall or security groups, DDoS protection from the host | ☐ Not Started | [DATE] |
| | Rate Limiting | Limits on authentication, public APIs, and model and media endpoints | ☐ Not Started | [DATE] |
| | Admin Surface | Admin endpoints not publicly reachable, or behind separate authentication | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Network configuration screenshots or infrastructure code
- [ ] Rate limit configuration

---

### CC6.7: Protecting Data in Transmission and Movement

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.7** | Encryption in Transit | TLS 1.2 or higher for clients, services, databases and vendors | ☐ Not Started | [DATE] |
| | Minimization at the Inference Boundary | Only the fields a prompt needs leave your system; documented in ARCHITECTURE-MAP.md page 4 | ☐ Not Started | [DATE] |
| | Data Export Control | Who can export customer data, and how exports are logged | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] TLS configuration or a scan result
- [ ] Prompt assembly code reviewed for data minimization
- [ ] Export log or procedure

---

### CC6.8: Preventing Unauthorized or Malicious Software

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC6.8** | Dependency Integrity | Lock files committed, dependency scanning, review of new packages | ☐ Not Started | [DATE] |
| | Endpoint Protection | Malware protection and automatic updates on work devices | ☐ Not Started | [DATE] |
| | Model and Artifact Provenance | Model weights and other binary artifacts only from trusted sources, in safe formats | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Dependency scan reports
- [ ] Endpoint protection status, dated

---

## CC7: System Operations

### CC7.1: Detecting Configuration Changes and New Vulnerabilities

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC7.1** | Vulnerability Scanning | Dependency and container scanning on every push, plus a scheduled run | ☐ Not Started | [DATE] |
| | Secret Scanning | Secret scanning in CI and push protection on the code host | ☐ Not Started | [DATE] |
| | Configuration Baseline | Infrastructure as code or a documented baseline, with drift checks | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Scan results over the audit period
- [ ] Configuration baseline and the last drift check

---

### CC7.2: Monitoring for Anomalies

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC7.2** | Security Event Logging | Authentication, admin and access events logged centrally | ☐ Not Started | [DATE] |
| | Alerting | Alerts on failed logins, privilege changes, error spikes and downtime | ☐ Not Started | [DATE] |
| | AI Usage Monitoring | Alerts on token or minute spikes, provider spend, and repeated injection attempts | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Alert configuration screenshots
- [ ] Examples of alerts that fired and what was done

---

### CC7.3: Evaluating Security Events

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC7.3** | Triage Criteria | Severity classification in INCIDENT-RESPONSE-PLAN.md | ☐ Not Started | [DATE] |
| | Event Log | Record of security events reviewed and the decision on each | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Security event log with triage decisions

---

### CC7.4: Responding to Security Incidents

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC7.4** | Incident Response Plan | INCIDENT-RESPONSE-PLAN.md, approved and current | ☐ Not Started | [DATE] |
| | Notification Procedure | Breach notification steps for customers, regulators and users | ☐ Not Started | [DATE] |
| | Plan Testing | Annual tabletop exercise, with notes | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Approved incident response plan
- [ ] Tabletop exercise record
- [ ] Incident records for any real incidents in the period

---

### CC7.5: Recovering from Security Incidents

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC7.5** | Recovery Procedures | Restore and rebuild steps in the incident response plan | ☐ Not Started | [DATE] |
| | Post-Incident Review | Root cause, fixes and lessons recorded within 7 days | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Post-incident reviews, with follow-up actions closed

---

## CC8: Change Management

### CC8.1: Authorizing, Testing, Approving and Implementing Changes

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC8.1** | Change Management Policy | CHANGE-MANAGEMENT-POLICY.md | ☐ Not Started | [DATE] |
| | Change Approval | Pull request record for every production change; self-review documented where you work alone | ☐ Not Started | [DATE] |
| | Automated Gates | Branch protection that blocks merge until tests and security checks pass | ☐ Not Started | [DATE] |
| | Deployment Record | Deploys only through the pipeline, with logs | ☐ Not Started | [DATE] |
| | Emergency Changes | Emergency change procedure with after-the-fact review | ☐ Not Started | [DATE] |
| | Prompt and Model Changes | System prompts version-controlled; model or provider swaps evaluated before release | ☐ Not Started | [DATE] |
| | Infrastructure Changes | Infrastructure changes made through code or recorded in the change log | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Sample of changes with request, test evidence, approval and deploy record
- [ ] Branch protection settings screenshot
- [ ] Prompt and model change log with evaluation results
- [ ] Emergency changes reviewed after the fact

---

## CC9: Risk Mitigation

### CC9.1: Mitigating Business Disruption

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC9.1** | Continuity Plan | Disaster recovery plan with RTO and RPO (INFORMATION-SECURITY-POLICY.md section 11) | ☐ Not Started | [DATE] |
| | Provider Contingency | Named fallback for each critical AI, media and hosting provider | ☐ Not Started | [DATE] |
| | Insurance | Cyber insurance decision, recorded either way | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Recovery plan, approved
- [ ] Contingency vendors listed in SUBPROCESSOR-TABLE.md

---

### CC9.2: Managing Vendor and Business Partner Risk

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **CC9.2** | Vendor Inventory | SUBPROCESSOR-TABLE.md, matching ARCHITECTURE-MAP.md page 6 | ☐ Not Started | [DATE] |
| | Pre-Onboarding Assessment | VENDOR-ASSESSMENT.md completed before customer data flows | ☐ Not Started | [DATE] |
| | Contracts | DPA or equivalent terms signed with every processor | ☐ Not Started | [DATE] |
| | Vendor Report Review | Annual review of each critical vendor's SOC 2 report: scope, period, exceptions, complementary user entity controls | ☐ Not Started | [DATE] |
| | AI Data Terms | Training default, retention default and zero-retention status recorded per AI vendor | ☐ Not Started | [DATE] |
| | Vendor Offboarding | Data deletion confirmed when a vendor is removed | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Vendor inventory with risk ratings
- [ ] Completed assessments and signed DPAs
- [ ] Dated notes from each vendor report review, including the user entity controls you implemented
- [ ] Bridge letters where a vendor's report period ended more than a few months ago

---

## A1: Availability (Optional Category)

### A1.1: Capacity Management

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **A1.1** | Capacity Monitoring | Database, compute and connection usage monitored against limits | ☐ Not Started | [DATE] |
| | Provider Quotas | AI and media provider rate limits, concurrency caps and quotas tracked, with alerts before you hit them | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Capacity dashboards and alert thresholds
- [ ] Provider quota settings, dated

---

### A1.2: Environmental Protections, Backups and Recovery Infrastructure

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **A1.2** | Backups | Automated, encrypted backups with defined retention | ☐ Not Started | [DATE] |
| | Recovery Infrastructure | Where you would restore to, and how | ☐ Not Started | [DATE] |
| | Environmental Protections | Inherited from hosting provider | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Backup configuration and job history

---

### A1.3: Testing Recovery Procedures

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **A1.3** | Restore Test | A real restore from backup, timed and recorded, at least annually | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Restore test record with time to recover against your RTO

---

## C1: Confidentiality (Optional Category)

### C1.1: Identifying and Protecting Confidential Information

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **C1.1** | Classification | Data classification in INFORMATION-SECURITY-POLICY.md section 3 | ☐ Not Started | [DATE] |
| | Confidential Data Inventory | Where confidential data lives (ARCHITECTURE-MAP.md page 5) | ☐ Not Started | [DATE] |
| | Key Management | Who and what can use encryption keys; rotation schedule | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Classification policy and store inventory
- [ ] Key access list

---

### C1.2: Disposing of Confidential Information

| Criteria | Control | Evidence Source | Status | Last Verified |
|----------|---------|-----------------|--------|---|
| **C1.2** | Retention Schedule | DATA-RETENTION-POLICY.md | ☐ Not Started | [DATE] |
| | Deletion with Evidence | Deletion jobs logged, backups aged out, vendor deletion confirmed | ☐ Not Started | [DATE] |

**Evidence:**
- [ ] Deletion logs over the period
- [ ] Vendor deletion confirmations

---

## PI1: Processing Integrity (Optional Category)

Most AI products leave this category out, because it asks you to commit that processing is complete, valid, accurate and timely. Include it only if a customer needs that commitment for a specific, deterministic part of your system (billing, scoring, data pipelines), and scope it to that part.

| Criteria | What it covers | Control | Evidence Source | Status | Last Verified |
|----------|---|---------|-----------------|--------|---|
| **PI1.1** | Definitions of data processed and product specifications | Specification for the in-scope processing | [SOURCE] | ☐ Not Started | [DATE] |
| **PI1.2** | Controls over system inputs | Input validation and completeness checks | [SOURCE] | ☐ Not Started | [DATE] |
| **PI1.3** | Controls over processing | Processing checks, reconciliation | [SOURCE] | ☐ Not Started | [DATE] |
| **PI1.4** | Complete, accurate, timely output | Output checks and delivery monitoring | [SOURCE] | ☐ Not Started | [DATE] |
| **PI1.5** | Storage of inputs, items in processing and outputs | Storage controls and retention | [SOURCE] | ☐ Not Started | [DATE] |

---

## P1 to P8: Privacy (Optional Category)

The Privacy category has 18 criteria in eight groups. It overlaps heavily with what privacy law already asks of you, which is why some companies add it, and it is also the largest single addition to an audit.

| Criteria | Group | What it covers | Control | Evidence Source | Status | Last Verified |
|----------|---|---|---------|-----------------|--------|---|
| **P1.1** | Notice | Privacy notice provided and kept current | Privacy policy; AI interaction notice in the interface | PRIVACY-POLICY-TEMPLATE.md | ☐ Not Started | [DATE] |
| **P2.1** | Choice and consent | Choices communicated; explicit consent where needed | Consent flows for voice, biometric, marketing and AI training | [SOURCE] | ☐ Not Started | [DATE] |
| **P3.1** | Collection | Collection limited to stated objectives | Data minimization review | [SOURCE] | ☐ Not Started | [DATE] |
| **P3.2** | Collection | Explicit consent obtained before collecting data that needs it | Consent captured before voice or biometric collection | [SOURCE] | ☐ Not Started | [DATE] |
| **P4.1** | Use, retention, disposal | Use limited to stated purposes | Purpose list matched to processing | [SOURCE] | ☐ Not Started | [DATE] |
| **P4.2** | Use, retention, disposal | Retention consistent with objectives | DATA-RETENTION-POLICY.md | [SOURCE] | ☐ Not Started | [DATE] |
| **P4.3** | Use, retention, disposal | Secure disposal | Deletion logs | [SOURCE] | ☐ Not Started | [DATE] |
| **P5.1** | Access | Data subjects can access their data | Access request procedure and export | [SOURCE] | ☐ Not Started | [DATE] |
| **P5.2** | Access | Corrections made and passed on | Correction procedure | [SOURCE] | ☐ Not Started | [DATE] |
| **P6.1** | Disclosure and notification | Disclosure to third parties as consented | Subprocessor list, consent records | [SOURCE] | ☐ Not Started | [DATE] |
| **P6.2** | Disclosure and notification | Record of authorized disclosures | Disclosure log | [SOURCE] | ☐ Not Started | [DATE] |
| **P6.3** | Disclosure and notification | Record of unauthorized disclosures and breaches | Incident log | [SOURCE] | ☐ Not Started | [DATE] |
| **P6.4** | Disclosure and notification | Privacy commitments from vendors, assessed periodically | DPAs and vendor reviews | [SOURCE] | ☐ Not Started | [DATE] |
| **P6.5** | Disclosure and notification | Vendors commit to notify you of unauthorized disclosure | Breach notice clauses in DPAs | [SOURCE] | ☐ Not Started | [DATE] |
| **P6.6** | Disclosure and notification | Breach notification to data subjects, regulators and others | Notification procedure | [SOURCE] | ☐ Not Started | [DATE] |
| **P6.7** | Disclosure and notification | Accounting of data held and disclosed, on request | Access request response template | [SOURCE] | ☐ Not Started | [DATE] |
| **P7.1** | Quality | Personal data kept accurate and complete | Profile editing, validation | [SOURCE] | ☐ Not Started | [DATE] |
| **P8.1** | Monitoring and enforcement | Inquiries, complaints and disputes handled; compliance monitored | Privacy contact, complaint log | [SOURCE] | ☐ Not Started | [DATE] |

---

## Complementary Controls: What You Inherit and What You Owe

A solo founder's SOC 2 leans on other companies' controls, and the report says so explicitly. Two terms come up in every engagement.

**Subservice organizations.** Your hosting provider, database host, and AI and media providers operate controls you depend on. Almost every small company uses the carve-out method: your report describes what those providers do and excludes their controls from testing. The auditor then expects you to have read each provider's own SOC 2 report and to monitor them (CC9.2).

**Complementary user entity controls (CUECs).** Each vendor's SOC 2 report lists controls its customers must operate for the vendor's controls to work, such as enabling MFA on your account, managing your own API keys, or configuring retention. Read that section of every critical vendor's report and record which ones you do. Your own report will carry a CUEC list for your customers too, so draft it as you go.

| Vendor | Report Type and Period | Exceptions Noted | CUECs You Must Operate | Implemented? | Reviewed |
|---|---|---|---|---|---|
| [HOSTING PROVIDER] | [TYPE II, PERIOD] | [NONE / LIST] | [LIST] | [YES / PARTLY / NO] | [DATE] |
| [AI PROVIDER] | [TYPE II, PERIOD] | [NONE / LIST] | [LIST] | [YES / PARTLY / NO] | [DATE] |
| [ADD ROWS] | | | | | |

---

## Control Effectiveness Assessment

### Testing and Validation

For each control implemented, evidence must demonstrate:

1. **Existence:** the control is documented and in place
2. **Execution:** the control is actually being performed
3. **Effectiveness:** the control is achieving its objective

| Control | Evidence of Existence | Evidence of Execution | Evidence of Effectiveness | Last Tested |
|---------|---|---|---|---|
| Access Control (CC6.1, CC6.3) | IAM policy document | Quarterly access review records | Review found and removed stale access, or confirmed none | [DATE] |
| Encryption (CC6.1, CC6.7) | Encryption policy | Store and TLS configuration | Configuration scan shows no unencrypted store or endpoint | [DATE] |
| Change Management (CC8.1) | Change policy, branch protection | Pull requests and deploy logs | Sample shows every production change went through the pipeline | [DATE] |
| Backup and Recovery (A1.2, A1.3) | Recovery plan, RTO and RPO | Backup job history | Restore test completed in [X] hours | [DATE] |
| Vendor Management (CC9.2) | Vendor inventory | Assessments and report reviews | Every critical vendor reviewed within the year | [DATE] |

---

## SOC 2 Audit Readiness Checklist

**Before a Type I** (controls designed and in place on one date):

- [ ] Categories chosen and the system boundary defined
- [ ] Every in-scope criterion has at least one control with evidence
- [ ] Policies approved and acknowledged
- [ ] Vendor inventory complete, DPAs signed, critical vendor reports reviewed
- [ ] Service commitments and system requirements written down
- [ ] Risk assessment completed and dated

**Before a Type II** (controls operating over a period, commonly 3 to 12 months; first reports are often 3 to 6):

- [ ] Everything in the Type I list
- [ ] Evidence collected continuously across the whole observation window
- [ ] Recurring controls show every occurrence (each quarterly access review, each restore test)
- [ ] Incident response plan exercised at least once
- [ ] Significant deficiencies remediated before the window starts

---

## Audit Scope and Timeline

| Item | Details |
|------|---------|
| Report Type | [SOC 2 Type I / SOC 2 Type II] |
| System in Scope | [YOUR APP], infrastructure in [YOUR CLOUD PROVIDER] |
| Categories | Security (CC1 to CC9) [+ A1] [+ C1] [+ PI1] [+ P1 to P8] |
| Subservice Organizations | [LIST, CARVED OUT] |
| Point in Time or Period | [DATE] or [DATE] to [DATE] |
| Auditor | [CPA FIRM NAME] |
| Fieldwork Start | [DATE] |
| Expected Report Date | [DATE] |

---

## Annual SOC 2 Maintenance

| Frequency | Task | Owner | Next Date |
|-----------|------|-------|-----------|
| Quarterly | Control self-assessment (walk this file) | Security Lead | [DATE] |
| Quarterly | Risk register and regulatory review | Compliance Lead | [DATE] |
| Quarterly | Access review | Security Lead | [DATE] |
| Annually | Vendor report reviews and DPA check | Compliance Lead | [DATE] |
| Annually | Restore test and tabletop exercise | Security Lead | [DATE] |
| Annually | External SOC 2 examination | [CPA FIRM NAME] | [DATE] |

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
