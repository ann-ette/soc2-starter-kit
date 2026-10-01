# Security & Trust Page

**Company:** [YOUR COMPANY]
**Product:** [YOUR APP]
**Version:** 1.0
**Last Updated:** [DATE]

---

## Team Size Adaptation

This page is a public-facing document (not internal). If you reference security roles or team members, use descriptive titles that work for any team size. For example: "Our security practices include..." or simply avoid role names. The security commitments are the same regardless of team size.

<!-- CUSTOMIZE: Read this before you publish anything below.

     Every line on this page is a public claim about your company, and a security page that
     overstates your controls is a deceptive statement to the customers who rely on it. Delete
     every line you cannot evidence today. The optional blocks are commented out so that nothing
     unearned ships by default; uncomment a block only when the thing it describes is true.

     A short page with five true lines does more for you than a long page with fifty hopeful ones. -->

---

## Trust & Security Commitments

[YOUR COMPANY] builds [YOUR APP] to protect the data our customers trust us with. This page describes the controls we operate today and the ones we are working toward, and it says which is which.

---

## 🔐 Security Overview

### Our Security Posture

<!-- CUSTOMIZE: Only list certifications and reports you actually have or are actively pursuing.
     Claiming a report or certification you haven't completed creates legal liability. Use
     "in progress" or "controls implemented" language until you have a completed audit report.
     SOC 2 produces an attestation report, so say "SOC 2 Type II report," never "SOC 2 certified." -->

**[YOUR COMPANY] security standards:**

- **SOC 2 Trust Services Criteria**: Controls implemented; formal examination planned for [DATE]
- **GDPR**: Privacy controls aligned with European data protection requirements
- **CCPA**: Privacy controls aligned with California consumer privacy requirements

<!-- Add these lines ONLY when they are true:
- ✓ **Continuous Security Scanning**: Automated vulnerability and secret scanning on every code change
- ✓ **SOC 2 Type I**: Report issued [DATE] by [CPA FIRM]
- ✓ **SOC 2 Type II**: Report covering [PERIOD], issued [DATE] by [CPA FIRM]
- ✓ **ISO/IEC 27001**: Certified [DATE] by [CERTIFICATION BODY]
- ✓ **Penetration Testing**: Last completed [DATE] by [FIRM]
-->

---

## 🛡️ Data Protection

### Encryption
- **In Transit**: All data transmitted via TLS 1.2 or higher (HTTPS)
- **At Rest**: Data stored with [AES-256] encryption at [YOUR DATABASE] and [OBJECT STORAGE]
- **Backups**: Backups encrypted [and stored in a separate region]

### Access Control
- **Authentication**: Multi-factor authentication (MFA) on every administrative account
- **Authorization**: Access granted on least privilege and reviewed [QUARTERLY]
- **Audit Logging**: Administrative access logged

### Infrastructure Security
- **Cloud Provider**: Hosted on [YOUR CLOUD PROVIDER], which holds its own SOC 2 Type II report
- **Network Isolation**: Databases and internal services not reachable from the public internet
- **Automated Backups**: [DAILY] encrypted backups

---

## 🤖 AI and Your Data

<!-- CUSTOMIZE: Buyers now ask these questions before any others. Answer each one from your
     vendors' current terms, and re-check them whenever a provider changes its policy. Training
     and retention are separate questions: a provider that does not train on your data may still
     store it. -->

| Question | Our Answer |
|---|---|
| Which AI providers process your content? | [LIST, e.g. LLM provider, speech provider, voice provider] |
| Is your content used to train AI models? | [No. Our providers' business terms exclude it / Only with your opt-in] |
| How long do AI providers keep your content? | [PROVIDER DEFAULT, e.g. up to 30 days for abuse monitoring / zero retention enabled] |
| Do people at the provider review your content? | [ANSWER FROM PROVIDER TERMS] |
| Will you always know you are talking to an AI? | [Yes. The interface says so where every conversation starts] |
| Is generated content marked as AI-generated? | [ANSWER, where required] |

---

## 🚨 Availability & Reliability

<!-- CUSTOMIZE: Publish an uptime number only if your terms of service commit to it. For reference,
     99.9% allows about 43 minutes of downtime in a 30-day month; 99.95% allows about 22. If you do
     not offer an SLA, delete the table and keep the status page line. -->

### Service Level Agreement (SLA)

| Metric | Commitment |
|--------|------------|
| **Uptime** | [99.9%] ([about 43 minutes] of downtime in a 30-day month) |
| **Recovery Time Objective (RTO)** | [TARGET] |
| **Recovery Point Objective (RPO)** | [TARGET] |

### Monitoring & Incident Response
- **Monitoring**: Automated alerts on errors, downtime and security events
- **Incident Response**: Security incidents triaged within [X hours]
- **Status Page**: [STATUS PAGE URL]
- **Recovery Testing**: Restore from backup tested [FREQUENCY]

---

## 🔑 How Our Controls Map to SOC 2

The Security category of SOC 2 has nine groups of common criteria. This is the shape of our program against them; the detail is available to customers under NDA.

| Criteria | What It Covers | How We Address It |
|---------|---------|---|
| **CC1** | Control environment | [Code of conduct, defined roles, security training] |
| **CC2** | Communication and information | [This page, our privacy policy, a published vulnerability reporting channel] |
| **CC3** | Risk assessment | [Risk register reviewed quarterly, AI-specific risks included] |
| **CC4** | Monitoring activities | [Quarterly control self-assessment, tracked remediation] |
| **CC5** | Control activities | [Written policies, technology controls] |
| **CC6** | Logical and physical access | [MFA, least privilege, quarterly access reviews, encryption] |
| **CC7** | System operations | [Vulnerability and secret scanning, monitoring, incident response] |
| **CC8** | Change management | [Every change reviewed, tested and deployed through a pipeline] |
| **CC9** | Risk mitigation | [Vendor assessments, DPAs, continuity planning] |

---

## 🏢 Vendor Security Management

We assess vendors before they receive customer data, and we keep a Data Processing Agreement (DPA) with every vendor that processes personal data on our behalf.

### Subprocessors

<!-- CUSTOMIZE: List your actual subprocessors, from SUBPROCESSOR-TABLE.md. Publish only what each
     vendor's own documentation supports, and date the list. -->

| Vendor | Service | Data Shared | Location | Last Reviewed |
|--------|---------|---|---|---|
| [VENDOR] | [LLM / speech / voice / hosting / payments] | [DATA CATEGORIES] | [REGION] | [DATE] |
| [VENDOR] | [SERVICE] | [DATA CATEGORIES] | [REGION] | [DATE] |
| [ADD ROWS] | | | | |

We give customers [30 days'] notice before adding a subprocessor that processes their personal data.

---

## 🔍 Compliance Standards

### Privacy Regulations

#### GDPR (Europe)
- Data Processing Agreements available to customers
- Data subject rights supported (access, correction, deletion, portability, objection)
- Personal data breaches reported to the supervisory authority within 72 hours where the GDPR requires it, and to affected people without undue delay where the risk to them is high
- **Contact:** [YOUR EMAIL]

#### CCPA (California)
- Consumer privacy rights supported (know, delete, correct, opt out of sale or sharing, limit use of sensitive personal information)
- Privacy notice published
- **Contact:** [YOUR EMAIL]

#### Other Jurisdictions

<!-- CUSTOMIZE: List only the laws you have actually assessed your product against, e.g. UK GDPR,
     Canada's PIPEDA, Australia's Privacy Act, other US state privacy laws, HIPAA if you sign BAAs.
     A checkmark here is a claim of compliance. -->

- [LAW]: [WHAT YOU DO]

### Industry Standards

| Standard | How We Use It |
|----------|-------|
| **OWASP Top 10 (2025)** | Web application security testing reference |
| **OWASP Top 10 for LLM Applications (2025)** | AI feature threat model reference |
| **OWASP Top 10 for Agentic Applications (2026)** | Threat model reference for features where a model calls tools or acts for a user |
| **MITRE ATLAS** | Catalogue of attacker techniques against AI systems, used when testing AI features |
| **Payments** | Card data handled entirely by [PAYMENT PROCESSOR]; it never touches our servers |

---

## 🛠️ Secure Development Practices

### Code Security
- **Change Review**: [Every change reviewed by a second engineer / Every change passes automated tests and security checks before merge]
- **Dependency Scanning**: Automated scanning for vulnerable libraries
- **Secret Scanning**: Automated scanning for credentials in code
- **No Secrets in Code**: Secrets kept in [SECRET MANAGER], never in source control

<!-- Add ONLY if true:
- **Static Analysis (SAST)**: Automated code scanning on every change
- **Signed Commits**: Commit signing enforced on the production branch
-->

### Deployment & Change Management
- **Change Control**: Production changes deployed through a pipeline with a record of each deploy
- **Testing**: Changes tested before production
- **Rollback**: [Rollback procedure for failed deployments]

### Vulnerability Management
- **Patching**: Critical patches applied within [7 days]
- **Vulnerability Scanning**: [FREQUENCY] automated scans
- **Responsible Disclosure**: See below, and [`/.well-known/security.txt`](https://[YOUR DOMAIN]/.well-known/security.txt)

<!-- Add ONLY if true:
- **Penetration Testing**: Third-party penetration test [ANNUALLY], last completed [DATE]
-->

---

## 🔒 Data Retention & Deletion

**We delete data according to the following schedule:**

| Data Type | Retention | Deletion Method |
|---|---|---|
| **User Accounts** | Until deletion, then a [30-day] grace period | Deleted from the database; removed from backups as they age out |
| **Conversation Data** | [X] months (or on your request) | Automated deletion after retention expires |
| **Voice Recordings** | [X] days [or not stored] | Automatic deletion after retention expires |
| **Backups** | [PERIOD] | Automated lifecycle deletion |
| **Payment Records** | [PERIOD REQUIRED BY TAX LAW IN YOUR JURISDICTION] | Retained by [PAYMENT PROCESSOR] and in our accounting records |

**Your Rights:** You can request deletion at any time (see our [Privacy Policy](#)).

---

## 📋 Incident Response & Breach Notification

### Our Incident Response Commitment

- **Detection**: Automated monitoring and alerting
- **Response**: Security incidents triaged within [X hours]
- **Investigation**: Root cause analysis for every security incident
- **Notification**: Affected customers notified without undue delay [and within the period your contracts and applicable law require]
- **Post-Incident Review**: Lessons learned recorded and acted on

### What Happens If a Breach Occurs

**We will:**
1. Investigate and contain the breach
2. Assess what data was accessed and by whom
3. Notify regulators where the law requires it (under the GDPR, within 72 hours of becoming aware), and notify affected customers and users as the law and our contracts require
4. Tell you what we know and what you can do to protect yourself
5. Fix the cause and record what we changed

**Your Rights:** See our [Privacy Policy](#) for your rights in case of a breach.

---

## 📞 Responsible Disclosure

If you discover a security vulnerability, please report it to us privately so we can fix it before it is published.

### Report a Vulnerability

**Email:** [SECURITY@YOUR DOMAIN]
**Machine-readable contact:** `https://[YOUR DOMAIN]/.well-known/security.txt` (RFC 9116)

**Include:**
- Description of the vulnerability
- Affected component or endpoint
- Steps to reproduce
- Potential impact
- How to reach you

**Our Commitment:**
- Acknowledge receipt within [X business days]
- Keep you updated while we investigate
- Credit you in the fix notes if you want credit

<!-- Add ONLY if you run one:
**Bug Bounty:** [PROGRAM DETAILS AND SCOPE]
-->

---

## 🎓 Security Awareness & Training

- Everyone with access to customer data completes security training [ANNUALLY]
- Topics include phishing, credential handling, data protection, and the safe use of AI tools with customer data

---

## 📜 Compliance Documentation

### Available Upon Request

<!-- CUSTOMIZE: List only documents that exist. SOC 2 reports are restricted-use and are shared
     under NDA; there is no public registry where anyone can look one up. -->

- **Data Processing Agreement (DPA)**
- **Security Questionnaire Responses**
- **Subprocessor List**

<!-- Add ONLY when they exist:
- **SOC 2 Type II Report** (under NDA)
- **ISO/IEC 27001 Certificate**
- **Penetration Test Summary**
- **Business Associate Agreement (BAA)** (if you handle protected health information and sign BAAs)
-->

**Request Documentation:** [COMPLIANCE@YOUR DOMAIN]

---

## 🔗 Security Links

- **[Privacy Policy](#)**: How we collect and use your data
- **[Terms of Service](#)**: Legal terms of service
- **[Subprocessor List](#)**: Who processes data on our behalf
- **[Status Page](#)**: Real-time service status

---

## 📞 Contact Us

### Security Inquiries
- **Email:** [SECURITY@YOUR DOMAIN]

### Privacy Questions
- **Email:** [YOUR EMAIL]
- **Mailing Address:** [YOUR ADDRESS]

---

## 🔄 Updates & Changes

We review this page whenever our controls, vendors or certifications change, and at least [every six months]. Changes take effect on the date below.

**Last Updated:** [DATE]
**Next Review:** [DATE]

---

## 📊 Security Metrics (Optional)

<!-- CUSTOMIZE: Publish only metrics you measure and are willing to keep publishing. Delete this
     section otherwise. Do not copy example numbers. -->

| Metric | Last 12 Months |
|--------|-------|
| Uptime | [MEASURED VALUE] |
| Security Incidents | [MEASURED VALUE] |

---

## ✅ How You Can Check Our Claims

1. **TLS and certificate:** run our domain through [SSL Labs](https://www.ssllabs.com/ssltest/)
2. **Security headers:** run our domain through [securityheaders.com](https://securityheaders.com/)
3. **Vulnerability contact:** fetch `https://[YOUR DOMAIN]/.well-known/security.txt`
4. **SOC 2 report:** request it from [COMPLIANCE@YOUR DOMAIN]; we share it under NDA <!-- CUSTOMIZE: delete this line until a report exists -->

---

## 📋 Revision History

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0 | [DATE] | Initial security page | [YOUR NAME] |
| | | | |

---

If you have questions about our security practices, contact us at [SECURITY@YOUR DOMAIN].

*Last Updated: [DATE]* | *[YOUR COMPANY]*
