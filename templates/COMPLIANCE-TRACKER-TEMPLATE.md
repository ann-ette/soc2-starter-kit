# SOC 2 Compliance Tracker Template

This document describes the recommended structure for a SOC 2 compliance tracking spreadsheet. Create a spreadsheet file (Excel, Google Sheets, or equivalent) with the following four sheets and column structure.

---

## Sheet 1: Remediation Tracker

**Purpose:** Track security findings, vulnerabilities, and remediation efforts.

**Column Definitions:**

| Column | Type | Description |
|--------|------|-------------|
| **ID** | Text | Unique identifier (e.g., VULN-001, FINDING-042) |
| **Category** | Dropdown | Classification: Security Vulnerability, Control Gap, Configuration Issue, Process Gap, Other |
| **Item** | Text | Title/description of the finding or vulnerability |
| **Severity** | Dropdown | Critical, High, Medium, Low, Informational |
| **Status** | Dropdown | Open, In Progress, Pending Review, Resolved, Accepted Risk, Deferred |
| **Owner** | Text | Team member or role responsible for remediation |
| **Target Date** | Date | Expected completion date for remediation |
| **Evidence Link** | Text/URL | Link to GitHub issue, PR, commit, or documentation artifact |
| **Notes** | Text | Additional context, blockers, or risk acceptance rationale |

**Example Rows:**

| ID | Category | Item | Severity | Status | Owner | Target Date | Evidence Link | Notes |
|----|----------|------|----------|--------|-------|-------------|---------------|-------|
| VULN-001 | Security Vulnerability | Outdated lodash version in package.json | High | Resolved | DevOps Lead | 2026-04-05 | PR #147 | Updated to 4.17.21, tested in staging |
| FINDING-001 | Control Gap | No secrets scanning in CI/CD | Critical | In Progress | Security Engineer | 2026-04-10 | https://github.com/org/repo/issues/45 | Implementing Gitleaks in GitHub Actions |
| FINDING-002 | Configuration Issue | .env file committed to main branch | Critical | Resolved | Backend Engineer | 2026-03-28 | Commit abc123def | Added to .gitignore, rotated exposed credentials |
| FINDING-003 | Process Gap | No documented incident response procedure | High | Pending Review | Security Lead | 2026-04-15 | Google Drive link | Draft completed, awaiting stakeholder approval |
| CONFIG-001 | Control Gap | Missing HSTS headers | Medium | In Progress | Frontend Lead | 2026-04-20 | PR #150 | Implementing security headers in nginx config |

---

## Sheet 2: Vendor DPA Status

**Purpose:** Track third-party vendors, data sharing, and Data Processing Agreements (DPAs).

**Column Definitions:**

| Column | Type | Description |
|--------|------|-------------|
| **Vendor** | Text | Name of third-party vendor or SaaS provider |
| **Data Shared** | Text | Type of data provided to vendor (e.g., customer data, transaction logs, analytics) |
| **SOC 2 Status** | Dropdown | Certified, Pending, N/A, Not Available |
| **DPA Status** | Dropdown | Signed, Pending, N/A, Not Needed |
| **Last Reviewed** | Date | Date of most recent security/compliance review |
| **Next Review** | Date | Scheduled date for next review |
| **Action Needed** | Text | Any pending items (e.g., "Request SOC 2 report", "Send DPA for signature") |

**Example Rows:**

| Vendor | Data Shared | SOC 2 Status | DPA Status | Last Reviewed | Next Review | Action Needed |
|--------|-------------|--------------|-----------|---------------|-------------|---------------|
| Auth0 | Customer identity, authentication logs | Certified | Signed | 2026-03-15 | 2026-06-15 | None |
| Stripe | Transaction data, payment methods | Certified | Signed | 2026-02-20 | 2026-05-20 | Review DPA renewal terms |
| CloudFlare | DNS, WAF logs | Certified | Signed | 2026-01-10 | 2026-04-10 | Schedule annual review |
| Datadog | Application logs, metrics, traces | Certified | Pending | 2026-03-01 | 2026-06-01 | Send executed DPA to legal |
| SendGrid | Customer email addresses, delivery logs | Certified | N/A | 2026-02-28 | 2026-05-28 | Review processor addendum |
| Custom API Partner | Internal transaction logs | N/A | Pending | 2026-03-20 | 2026-06-20 | Obtain DPA + SOC2 report from partner |

---

## Sheet 3: Evidence Log

**Purpose:** Maintain an audit trail of compliance evidence, controls, and supporting documentation.

**Column Definitions:**

| Column | Type | Description |
|--------|------|-------------|
| **Date** | Date | Date evidence was created or artifact generated |
| **Control Area** | Dropdown | SOC 2 trust service category: CC (Change & Config), PO (Policies), PT (Processors), SC (Security), A&A (Access & Availability), etc. |
| **Evidence Type** | Dropdown | Policy Document, Scan Report, Audit Log, Test Result, Approval/Sign-off, Process Documentation, Training Record, Incident Report, Configuration Snapshot |
| **Description** | Text | Brief description of the evidence |
| **Artifact Location** | URL/Text | Link to document, GitHub Actions artifact, Google Drive, or file path |
| **Reviewer** | Text | Person who validated or approved the evidence |
| **Notes** | Text | Retention policy, expiration date, or additional context |

**Example Rows:**

| Date | Control Area | Evidence Type | Description | Artifact Location | Reviewer | Notes |
|------|--------------|---------------|-------------|-------------------|----------|-------|
| 2026-03-20 | SC | Scan Report | Gitleaks secret detection run | Workflow run #1234 | Security Eng | Weekly automated scan, no secrets found |
| 2026-03-18 | CC | Process Documentation | Change management procedure | Google Drive: Policies > Change Mgmt | CTO | Latest version, approved 2026-03-15 |
| 2026-03-15 | SC | Test Result | NPM audit results | GitHub artifact npm-audit-report | DevOps Lead | 2 high-severity vulns identified, PR #145 opened |
| 2026-03-14 | PO | Policy Document | Information Security Policy | GitHub wiki > Policies | Security Lead | Annual review due 2026-03-14-2027 |
| 2026-03-10 | A&A | Training Record | Security awareness training | Employee tracker spreadsheet | HR | All engineers completed March 2026 training |
| 2026-03-05 | PT | Approval/Sign-off | DPA signed with Stripe | Legal folder: Vendor Agreements | Legal | Execution date 2026-03-05, good for 2 years |
| 2026-02-28 | SC | Configuration Snapshot | AWS security group audit | S3 bucket: evidence/aws-sg-2026-02 | Cloud Sec | Monthly baseline snapshot |

---

## Sheet 4: Review Schedule

**Purpose:** Track compliance review cadence and upcoming audit activities.

**Column Definitions:**

| Column | Type | Description |
|--------|------|-------------|
| **Review Item** | Text | Name of the control, process, or area to be reviewed |
| **Frequency** | Dropdown | Weekly, Monthly, Quarterly, Semi-Annually, Annually |
| **Last Completed** | Date | Date of most recent review/audit cycle |
| **Next Due** | Date | Calculated or scheduled date for next review |
| **Owner** | Text | Team member responsible for conducting the review |
| **Comments** | Text | Findings, action items, or notes from most recent review |

**Example Rows:**

| Review Item | Frequency | Last Completed | Next Due | Owner | Comments |
|-------------|-----------|-----------------|----------|-------|----------|
| Weekly Compliance Report | Weekly | 2026-03-31 | 2026-04-07 | Compliance Officer | Gitleaks scan passed, 0 secrets detected |
| CodeQL Security Scan | Weekly | 2026-03-25 | 2026-04-01 | Security Engineer | 3 medium-severity findings in Python code, created issues #200-202 |
| Access Control Audit | Monthly | 2026-03-15 | 2026-04-15 | Identity & Access | Quarterly cleanup of inactive accounts planned for April |
| Dependency Audit | Monthly | 2026-03-20 | 2026-04-20 | DevOps Lead | NPM and Pip audits clean, no high-severity vulns |
| Data Classification Review | Quarterly | 2026-01-15 | 2026-04-15 | Data Governance | New customer data types identified, updating classification matrix |
| Third-Party Vendor Audit | Quarterly | 2026-02-28 | 2026-05-28 | Procurement | Datadog DPA signature pending, follow-up scheduled |
| Security Policy Review | Semi-Annually | 2025-09-15 | 2026-03-15 | Security Lead | Spring review completed 2026-03-12, no changes required |
| External Audit / SOC 2 Assessment | Annually | 2025-03-01 | 2026-03-01 | CTO / Audit Team | Type II assessment scheduled for March 2026, fieldwork in progress |

---

## How to Use This Template

### Setup
1. Create a new spreadsheet (Excel, Google Sheets, or equivalent)
2. Create four sheets with the names shown above
3. Copy the column headers into each sheet
4. Add the example rows as reference data

### Maintenance
- **Weekly:** Review new findings from automated scans (Gitleaks, CodeQL, npm audit, pip audit); add to Remediation Tracker
- **Monthly:** Update Remediation Tracker status; run dependency audits; update Evidence Log with new artifacts
- **Quarterly:** Review Vendor DPA statuses; conduct access control audits; verify Review Schedule completion
- **Annually:** Complete SOC 2 assessment; review and renew policies; update vendor security posture

### Integration with GitHub Actions
- Automated workflows generate evidence artifacts (scan reports, audit logs)
- Link these artifacts in the **Evidence Log** sheet for traceability
- Use Evidence Log dates to track control operational effectiveness over time

### Export for Audits
- Print or export sheets to PDF for external auditor reviews
- Evidence Log serves as supporting documentation for SOC 2 Type II assessments
- Remediation Tracker shows how quickly issues are addressed

### Compliance Reporting
- Use Review Schedule to track control testing cycles
- Use Evidence Log to demonstrate evidence collection and retention
- Use Vendor DPA Status to show third-party risk management
- Use Remediation Tracker to show vulnerability management

---

## Key Principles

1. **Traceability:** Every finding and evidence item should have a source link (GitHub, cloud provider, etc.)
2. **Timeliness:** Update tracking spreadsheet within 1-2 business days of new evidence
3. **Ownership:** Assign clear owners to each item; avoid orphaned tasks
4. **Retention:** Keep all evidence for at least 2 years to support SOC 2 Type II extended observation period
5. **Automation:** Link automated scan outputs (GitHub Actions artifacts) to reduce manual data entry

---

## Related Documents

- **SOC 2 Trust Service Criteria:** Reference AICPA SOC 2 for control framework categories
- **GitHub Actions Workflows:** See `.github/workflows/` for automation that generates evidence
- **Security Policy:** Link to your Information Security Policy document
- **Incident Response Plan:** Link to IR documentation for incident tracking

