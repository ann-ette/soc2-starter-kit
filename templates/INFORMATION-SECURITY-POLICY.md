# Information Security Policy

**[YOUR COMPANY]**
**Version:** 1.0
**Effective Date:** [DATE]
**Last Reviewed:** [DATE]
**Owner:** [YOUR NAME / ROLE]

---

## 1. Purpose

This Information Security Policy establishes the security framework for [YOUR COMPANY] and the [YOUR APP] application. It defines the principles, responsibilities, and controls that govern how we protect information assets, customer data, and system integrity.

This policy draws on the control families of NIST SP 800-53 Revision 5 (Release 5.2.0, August 2025) and is mapped to the SOC 2 Trust Services Criteria in SOC2-CONTROL-MAPPING.md.

## 2. Scope

This policy applies to:

- All information systems operated by [YOUR COMPANY]
- All data processed, stored, or transmitted by [YOUR APP]
- All third-party services and subprocessors used in the delivery of [YOUR APP]
- All personnel with access to production systems (including the founder, contractors, and any future employees)

## 3. Information Classification

<!-- CUSTOMIZE: Adjust these classifications to match the types of data your app handles -->

| Classification | Description | Examples | Handling Requirements |
|---------------|-------------|----------|----------------------|
| **Public** | Information intended for public access | Marketing content, public documentation, App Store listing | No special handling required |
| **Internal** | Business information not intended for public access | Architecture diagrams, internal roadmaps, analytics dashboards | Access restricted to authorized personnel |
| **Confidential** | Sensitive business or user data | User accounts, conversation data, API keys, vendor contracts | Encrypted at rest and in transit; access logged; need-to-know basis |
| **Restricted** | Highly sensitive data requiring maximum protection | Authentication secrets, private keys, production database credentials | Encrypted, rotated regularly, never stored in code repositories |

## 4. Access Control

### 4.1 Principle of Least Privilege

All access to systems, data, and infrastructure is granted on a need-to-know basis with the minimum permissions required.

### 4.2 Authentication Requirements

<!-- CUSTOMIZE: List your actual authentication methods -->

- Production infrastructure: Multi-factor authentication (MFA) required
- Cloud provider console ([YOUR CLOUD PROVIDER]): MFA required
- Database access ([YOUR DATABASE]): Restricted to application service accounts and authorized admin access
- API keys and secrets: Stored in environment variables, never in source code
- Third-party vendor consoles: Individual accounts with MFA where supported

### 4.3 Access Reviews

Access to production systems is reviewed quarterly (or whenever team composition changes) to ensure:

- No unnecessary access exists
- Service accounts have minimum required permissions
- API keys and secrets are rotated on schedule
- Former contractors or team members have been deprovisioned

## 5. Data Protection

### 5.1 Encryption in Transit

All data transmitted between users, application servers, and third-party services uses TLS 1.2 or higher. Unencrypted HTTP connections are rejected or redirected to HTTPS.

### 5.2 Encryption at Rest

<!-- CUSTOMIZE: Document your actual encryption configuration -->

- **Database:** [YOUR DATABASE] provides AES-256 encryption at rest
- **File storage:** Any stored files are encrypted using provider-managed keys
- **Backups:** Database backups are encrypted using the same standards as primary storage

### 5.3 Secrets Management

- All API keys, database credentials, and authentication secrets are stored as environment variables in [YOUR CLOUD PROVIDER]
- Secrets are never committed to source control
- `.gitignore` includes `.env`, `.env.*`, `*.p8`, `*.pem`, `*.key`, and other secret file patterns
- Secret scanning is enabled via GitHub Actions (Gitleaks) to prevent accidental commits

## 6. Application Security

### 6.1 Input Validation

- All user input is validated and sanitized before processing
- Database queries use parameterized statements (never string concatenation)
- API endpoints validate request bodies using schema validation

### 6.2 Authentication and Session Management

<!-- CUSTOMIZE: Describe your actual auth implementation -->

- User authentication uses [Sign in with Apple / Google Sign-In / etc.] with JWT verification
- JWTs are validated for issuer, audience, and expiration
- Session tokens expire after [7 days / your actual expiry]

### 6.3 Dependency Management

- Dependencies are tracked via lock files (`package-lock.json`, `requirements.txt`)
- `npm audit` and `pip-audit` run automatically on every push via GitHub Actions
- Critical vulnerability alerts are reviewed within 72 hours and patched within 7 days

## 7. Infrastructure Security

<!-- CUSTOMIZE: Describe your actual hosting setup -->

### 7.1 Hosting Environment

[YOUR APP] is deployed on [YOUR CLOUD PROVIDER], which provides:

- Isolated container execution
- Managed TLS termination
- DDoS protection at the infrastructure level
- A current SOC 2 Type II report covering the infrastructure (obtain it and review it annually)

### 7.2 Database Security

[YOUR DATABASE] provides:

- Encryption at rest (AES-256)
- Encrypted connections (TLS)
- Automated backups
- Role-based access control

### 7.3 Network Security

- All external connections use HTTPS/TLS
- Database connections are restricted to application service accounts
- No direct public access to database or internal services

## 8. Vendor Management

### 8.1 Vendor Assessment

All third-party services that process, store, or transmit user data must undergo a security assessment before integration. The assessment evaluates:

- A SOC 2 Type II report, an ISO/IEC 27001 certificate, or an equivalent independent assessment
- Data Processing Agreement (DPA) availability
- Data retention and deletion policies
- Data residency and jurisdiction
- Incident notification commitments

### 8.2 Ongoing Monitoring

- Vendor security posture is reviewed annually
- DPA status is tracked in the Subprocessor Table
- Vendor security incidents are monitored via status pages and security advisories

See `SUBPROCESSOR-TABLE.md` for the complete vendor inventory.

## 9. Incident Response

[YOUR COMPANY] maintains a documented Incident Response Plan with:

- Severity classification (Sev 1–3)
- Detection, containment, eradication, recovery, and communication phases
- Notification timelines aligned with GDPR (72 hours), CCPA, and applicable regulations
- Post-incident review process

See `INCIDENT-RESPONSE-PLAN.md` for the full plan.

## 10. Change Management

All changes to production systems follow a documented change management process:

- **Standard changes:** Code review (or self-review for solo developers with documented rationale), automated testing, staged deployment
- **Significant changes:** Architecture review, risk assessment, rollback plan
- **Emergency changes:** Expedited review with post-deployment documentation within 24 hours

See `CHANGE-MANAGEMENT-POLICY.md` for the full process.

## 11. Business Continuity

### 11.1 Backup and Recovery

<!-- CUSTOMIZE: Document your actual backup configuration -->

- Database: Automated daily backups with [retention period] retention
- Application code: Version controlled in GitHub with full commit history
- Recovery time objective (RTO): [your target, e.g., 4 hours]
- Recovery point objective (RPO): [your target, e.g., 24 hours]

### 11.2 Disaster Recovery

In the event of a major infrastructure failure:

1. Assess the scope and impact
2. Communicate to affected users (if applicable)
3. Restore from backups to alternative infrastructure if primary provider is unavailable
4. Conduct post-incident review

## 12. Acceptable Use, Including AI Tools

- Company systems and customer data are used only for [YOUR COMPANY] business
- Customer data is never pasted into, uploaded to, or connected to an AI tool, browser extension or service that is not an approved vendor under a signed DPA (see `SUBPROCESSOR-TABLE.md`)
- Personal accounts are not used to store or process company or customer data
- Coding assistants and agents that can read the repository are approved tools, configured so they cannot read production secrets

<!-- CUSTOMIZE: List the AI tools you have approved for work use and what each may see. -->

## 13. AI Systems

- Every AI feature in [YOUR APP] is listed with its provider, model, purpose and the data it receives (`ARCHITECTURE-MAP.md` page 4)
- System prompts are kept in version control, and prompt or model changes follow `CHANGE-MANAGEMENT-POLICY.md`
- Users are told they are interacting with an AI system at the point of interaction
- AI features are tested against unsafe and adversarial conversations before each release (`RISK-REGISTER.md`, RISK-002 and RISK-017)

These four commitments are also the start of the AI policy, inventory and risk classification that ISO/IEC 42001 asks for; see `SOC2-GUIDE.md`.

## 14. Logging and Monitoring

- Authentication, administrative actions and access to customer data are logged
- Logs are retained for [PERIOD] and protected from edits by the people they record
- Alerts cover failed logins, privilege changes, error spikes, downtime and unusual AI usage or spend
- Alerts are reviewed when they fire, and log review is recorded [MONTHLY]

## 15. Devices and Training

- Work devices use full-disk encryption, a screen lock, automatic updates and malware protection
- Lost or stolen devices are reported immediately and their sessions revoked
- Everyone with access to customer data completes security awareness training at onboarding and annually

## 16. Violations

Violations of this policy are recorded and addressed. Consequences range from retraining to removal of access and termination of a contract or employment, depending on severity.

## 17. Policy Review

This policy is reviewed and updated:

- Annually (at minimum)
- After any significant security incident
- After major architectural changes
- After changes in applicable regulations

---

**Document History:**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [DATE] | [YOUR NAME] | Initial version |

---

<!-- CUSTOMIZE: Remove this comment block before publishing. Walk through each section and replace all placeholder values with your actual configuration. Sections marked with CUSTOMIZE comments require special attention. -->
