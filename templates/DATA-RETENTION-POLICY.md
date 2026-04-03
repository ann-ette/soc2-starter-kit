# Data Retention Policy

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME], Privacy Lead

---

## Team Size Adaptation

This template uses role names like "Privacy Lead" as a placeholder. For solo founders, you fill all these roles yourself — simply use your own name. For small teams (2–5), assign roles based on who handles privacy/compliance. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This policy defines retention periods and deletion procedures for all data types processed by [YOUR APP]. The policy complies with GDPR, CCPA, and industry best practices, ensuring customer data is retained only as long as necessary for business purposes.

<!-- CUSTOMIZE: Adjust retention periods based on your business, legal, and regulatory requirements -->

---

## Data Retention Table

| Data Type | Description | Retention Period | Legal Basis | Deletion Method | Notes |
|-----------|-------------|-----------------|-------------|-----------------|-------|
| **User Account Data** | Name, email, password hash, account creation date, last login | Until account deletion, minimum 30 days post-deletion | Contract (service provision), Consent | Encrypted deletion from [YOUR DATABASE], backups aged out | See Account Deletion SOP below. PII retained if user requests export. |
| **Conversation History / Chat Data** | User messages, AI responses, timestamps, metadata | [X] months from last activity, or user deletion request | Consent, Legitimate interest (service improvement) | Secure deletion from database and backups | Users can request deletion anytime via DSAR. AI training: never without explicit consent. |
| **Voice / Audio Recordings** | Raw audio files from voice API, transcriptions | [X] days to [X] weeks (balance: enough for support, minimal PII retention) | Consent, Legitimate interest (customer support) | Automatic deletion after retention period; encryption at rest | Must comply with voice API vendor retention policy (see SUBPROCESSOR-TABLE). |
| **Biometric Data** | Voice prints, facial recognition data (if collected) | Until withdrawal of consent or [X] days | Explicit Consent (high sensitivity) | Irreversible deletion via vendor; cannot be re-derived | Never retained longer than necessary. User has right to deletion anytime. |
| **Payment Data** | Credit card last-4 digits, billing address, payment method type | Until account deletion or end of contract | Contract (PCI compliance) | Tokenized via payment processor; never stored in [YOUR DATABASE] | PCI DSS compliance required. Full card data never retained. |
| **Transaction / Billing Records** | Invoice numbers, amounts, dates, payment status | 7 years (tax/legal retention) | Legal requirement (tax law, commerce law) | Archived to immutable storage post-7-year mark; encrypted | Retained for audit and legal purposes. Cannot be deleted per law. |
| **System & Application Logs** | API request logs, error logs, access logs, performance metrics | 90 days (hot), 1 year archive | Legitimate interest (security, troubleshooting) | Automated purge from hot storage; archive to cold storage | May contain PII (email addresses, user IDs). Anonymize or aggregate after 90 days where possible. |
| **Audit Logs** | Admin actions, permission changes, security events, failed access attempts | 1 year minimum (SOC 2 requirement) | Legal requirement (compliance), Legitimate interest (security) | Archived to immutable, encrypted cold storage | Critical for incident investigation. Longer retention for high-risk actions (e.g., data export). |
| **Backup Data** | Full database snapshots, application state, configuration | 30 days (recent), 1 year incremental | Legitimate interest (disaster recovery) | Delete from backup systems after retention; verify deletion | Encryption-in-transit and at rest required. Test restoration quarterly. |
| **Cached API Responses** | Responses from third-party APIs (LLM, translation, etc.) | [X] days (depends on API provider terms) | Consent, Legitimate interest (performance) | Automatic cache expiration; no manual deletion needed | Check vendor terms (some APIs prohibit caching). Do not cache PII. |
| **Analytics / Aggregated Data** | User behavior, feature usage, aggregated metrics | 24 months (rolling 2-year window) | Legitimate interest (product analytics) | Automated deletion of data >24 months old; retain only aggregated summaries | Anonymized, cannot be re-identified. Compliant with GDPR Article 11. |
| **Support Tickets / Help Center Logs** | Support conversations, help requests, resolution notes | 1 year post-closure, or user deletion request | Legitimate interest (customer support, legal protection) | Delete from ticketing system and backups after 1 year | May contain customer PII. Anonymize summaries before long-term archival. |
| **Email Communications** | Transactional emails, marketing emails, password reset links, security alerts | Transactional: until account deletion; Marketing: until unsubscribe | Consent (marketing), Contract (transactional) | Deleted from email system and backups per user retention above | Unsubscribe data retained per CAN-SPAM (1 year post-unsubscribe). |
| **IP Addresses / Device Identifiers** | User IP, device ID, browser fingerprint, geolocation | 90 days (rolling window) | Legitimate interest (security, fraud detection) | Anonymized or aggregated after 90 days | Used for abuse detection and access logs. Anonymization acceptable alternative to deletion. |
| **Third-Party Vendor Data** | Data shared with LLM provider, payment processor, analytics platform | Per vendor agreement and DPA; minimum: as long as service active | Contract (vendor terms), DPA requirements | Vendor responsible for deletion; [YOUR COMPANY] audit yearly | Refer to SUBPROCESSOR-TABLE for vendor-specific terms. Right to audit vendor deletion. |
| **Cookies / Web Tracking Data** | Session cookies, analytics cookies, ad cookies, consent preferences | Session (deleted on logout) or [X] days per cookie policy | Consent (per cookie consent banner) | Automatic deletion per expiration; user can clear via privacy controls | Document cookie types in Privacy Policy. Honor Do-Not-Track headers. |
| **Database Archives / Point-in-Time Backups** | Snapshots for disaster recovery, compliance audits | 30 days recent, 90 days incremental, 1 year full snapshots | Legitimate interest (disaster recovery, audit trail) | Delete via database snapshot schedule; verify immutable archive only | Test restoration to confirm backups are usable. Consider separate encryption key. |
| **User Consent Records** | Consent choices (marketing, analytics, voice training), consent timestamps, withdrawal history | Until withdrawal or account deletion; 3 years post-withdrawal for record-keeping | Consent, Legal requirement (GDPR, CCPA require proof of consent) | Archived if account deleted; retained if withdrawal | Proof of consent is legally required. Never delete audit trail. |
| **Security Incident Records** | Breach investigation data, forensics, incident reports, remediation actions | 3 years (per compliance standards) | Legal requirement (regulatory, litigation hold) | Archived to immutable storage; never deleted during hold period | Required for regulatory investigations, audits, and legal hold. |
| **User Settings & Preferences** | Notification settings, language, timezone, UI preferences, feature flags | Until account deletion | Contract (service personalization) | Deleted with account data | Non-sensitive; may be anonymized in aggregate analytics. |

---

## Data Deletion Procedures

### Account Deletion (User-Initiated)

**Retention Period:** 30 days (grace period for recovery); permanent deletion thereafter

**Deletion Steps:**
1. User requests deletion via account settings or [YOUR EMAIL]
2. Soft-delete: Mark account as "deleted" in [YOUR DATABASE], retain for 30 days
3. Send confirmation email with 30-day grace period and recovery link
4. Auto-purge after 30 days:
   - Encrypted deletion of user account, conversation history, voice data from [YOUR DATABASE]
   - Delete from backups (after backup rotation cycle completes, typically 30–90 days)
   - Request deletion confirmation from third-party vendors (LLM provider, payment processor, analytics)
5. Verify deletion: Query [YOUR DATABASE] to confirm no user records remain
6. Document deletion in audit log with timestamp and confirmation

**Exceptions:**
- Transaction records retained for 7 years (legal requirement)
- Audit logs retained for 1 year (security requirement)
- User consent records retained for 3 years post-deletion (regulatory proof)

---

### Conversation Data Deletion (User-Initiated or Automatic)

**Retention Period:** [X] months from last activity (<!-- CUSTOMIZE: 3 months, 6 months, etc. based on use case -->)

**Deletion Steps:**
1. User requests deletion via DSAR or account privacy settings
2. Query [YOUR DATABASE] for user conversations, metadata, and associated voice data
3. Encrypted deletion from primary database
4. Check for derived data (cached LLM responses, analytics summaries)
5. Request deletion from LLM vendor if data was used for fine-tuning
6. Delete from backups after rotation cycle (30–90 days)
7. Log deletion in audit trail with user ID, date, and count of deleted records

**Automatic Deletion (Post-Inactivity):**
- Cron job scheduled monthly: query for conversations >30 days old (<!-- CUSTOMIZE -->)
- Soft-delete first (mark as "inactive"), then hard-delete after 30-day grace period
- Alert user via email if data is about to be auto-deleted
- Document all automatic deletions with counts

---

### Backup Deletion

**Retention Period:** 30 days hot backup, 90 days incremental archive, 1 year full snapshot

**Deletion Steps:**
1. Automated backup rotation: daily backups purged after 30 days
2. Incremental backups: purged after 90 days
3. Monthly full snapshot: kept for 1 year, then deleted
4. Use [YOUR CLOUD PROVIDER] backup retention policies (e.g., AWS Backup retention rules)
5. Verify deletion from cold storage: list snapshots and confirm old dates are gone
6. Document: log snapshot deletion dates in backup audit trail

**Immutable Archive (1-Year Retention for Compliance):**
- One full snapshot per month stored in read-only S3 bucket with versioning disabled
- Encrypted with separate key; only compliance team has access
- Automatic deletion via lifecycle policy after 1 year

---

### Vendor Data Deletion

**Procedure:**
1. Maintain DPA with each vendor (LLM provider, payment processor, voice API, analytics)
2. DPA must specify: deletion timeline, data return/destruction option, certification of deletion
3. For each vendor, track:
   - Last data shared (date, record count)
   - Deletion request date
   - Vendor response deadline (typically 30 days)
   - Confirmation of deletion (vendor certification)
4. Quarterly audit: verify all vendors have deleted data within SLA
5. Document in SUBPROCESSOR-TABLE.md with deletion confirmation

---

### Cache and Temporary Data Deletion

**Automated Deletion:**
- In-memory cache: expires per TTL (<!-- CUSTOMIZE: e.g., 24 hours -->)
- Redis cache: automatic key expiration
- CDN cache: purge on content update or after [X] days
- Temporary upload files: deleted after [X] days or after processing complete

**Documentation:**
- Cache policy in code comments (<!-- CUSTOMIZE: expiration times -->)
- Cache invalidation logs in monitoring dashboard
- Verification: sample queries to confirm old cache entries are purged

---

## Retention Period Guidelines

<!-- CUSTOMIZE: Adjust based on business needs and legal requirements -->

| Category | Minimum | Maximum | Rationale |
|----------|---------|---------|-----------|
| **Customer Service** | 30 days | 1 year | Support investigation and dispute resolution |
| **Legal/Tax** | 7 years | 7 years | IRS, commerce law, regulatory requirements |
| **Security/Audit** | 1 year | 1 year | Incident investigation, SOC 2 compliance |
| **Backup/Disaster Recovery** | 30 days | 1 year | Business continuity, compliance archival |
| **Analytics** | 24 months | 24 months | Product insights, anonymized after 24 months |
| **Marketing/Consent** | Until unsubscribe | 3 years (post-unsubscribe) | CAN-SPAM, GDPR consent proof |
| **Voice/Biometric** | Until consent withdrawal | Until consent withdrawal | Minimize sensitive data retention |

---

## Legal Basis for Retention

| Basis | Data Types | Retention Justification |
|-------|-----------|------------------------|
| **Contractual Obligation** | User account, billing, support tickets, transaction records | Service provision, payment processing, customer support |
| **Legal Requirement** | Billing records (7 years), audit logs (1 year), consent records (3 years post-deletion) | Tax law, regulatory compliance (SOC 2, GDPR Article 6(1)(c)) |
| **Legitimate Interest** | Conversation history, analytics, system logs, device identifiers | Product improvement, fraud detection, security, performance optimization |
| **Consent** | Voice recordings, biometric data, marketing emails, analytics cookies | User has explicitly consented; can be withdrawn anytime |

---

## User Rights & Deletion Requests

### Data Subject Access Request (DSAR)

User has the right to request:
- Copy of all personal data retained about them
- Proof of retention basis
- List of recipients who have received their data
- Details on automated decision-making (if any)

**Response Timeline:** 30 days (GDPR requirement)

**Process:**
1. User emails [YOUR EMAIL] with "DSAR Request"
2. Verify user identity
3. Query [YOUR DATABASE] for all user data (account, conversations, voice, logs, consent records)
4. Compile export in standard format (CSV, JSON, or PDF)
5. Redact any third-party data or operational logs
6. Send export to user via secure link
7. Document DSAR in audit log (date, user ID, response date)

---

### Right to Deletion (Right to Be Forgotten)

User can request permanent deletion of all personal data except:
- Data legally required to be retained (tax records, audit logs)
- Data being used to establish/defend legal claims
- Data needed for another user's consent (e.g., shared conversation)

**Response Timeline:** 45 days (GDPR requirement)

**Process:**
1. User email [YOUR EMAIL] with "Deletion Request"
2. Confirm user identity
3. Execute account deletion procedure (see above)
4. Confirm completion to user within 45 days

---

### Right to Restrict Processing

User can request data processing be limited (not deleted). Examples:
- Retain for legal claims but stop analytics processing
- Retain voice data for customer support, but stop using for model training

**Implementation:**
- Flag user account with "processing restricted" status
- Stop sending data to analytics vendors
- Stop using data for model fine-tuning
- Continue retaining for legal/contractual purposes
- Document restriction in database

---

### Right to Data Portability

User can request data export in machine-readable format (CSV, JSON)

**Process:**
1. User requests via [YOUR EMAIL]
2. Export all user-created data (account, conversations, preferences)
3. Format: JSON or CSV per user preference
4. Encrypt export with user-provided password or secure link
5. Deliver within 30 days

---

## Monitoring & Compliance

### Automated Deletion Verification

- **Monthly:** Run query to verify deleted records are gone from primary database
- **Quarterly:** Verify deleted records removed from backups (sample old snapshots)
- **Quarterly:** Audit vendor deletion confirmations (check SUBPROCESSOR-TABLE updates)
- **Annual:** Full deletion compliance audit across all data types

### Logging & Audit Trail

All deletions must be logged:
```
DELETE_LOG = {
  "timestamp": "2026-04-03T14:30:00Z",
  "user_id": "user_12345",
  "data_type": "conversation_history",
  "record_count": 42,
  "deletion_method": "encrypted_delete",
  "initiated_by": "user_dsar_request", // or "auto_retention_expiry", "admin_request"
  "verified_by": "verification_query_at_2026-04-04",
  "status": "complete"
}
```

### Alerting

- Alert if automated deletion fails (e.g., database query timeout)
- Alert if DSAR/deletion request not completed within SLA
- Alert if backup deletion not confirmed within 90 days

---

## Annual Review

This policy must be reviewed annually:
- Confirm retention periods still align with business/legal needs
- Update vendor retention terms per DPA reviews
- Audit deletion logs for compliance
- Update procedures based on new vendor integrations
- Document policy version and change log

**Review Schedule:**
- **Date:** [DATE] (annually)
- **Responsible:** [YOUR NAME], Privacy Lead
- **Approval:** CEO/Founder

---

## Change Log

| Date | Change | Owner |
|------|--------|-------|
| [DATE] | Initial policy | [YOUR NAME] |
| [DATE] | Updated retention periods post-user research | [YOUR NAME] |

---

## Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Privacy Lead | [YOUR NAME] | _____________ | ________ |
| CEO / Founder | [YOUR NAME] | _____________ | ________ |

---

## Appendix: Data Classification

<!-- CUSTOMIZE: Adjust classifications based on your risk profile -->

| Classification | Examples | Encryption Required | Deletion Priority |
|----------------|----------|-------------------|------------------|
| **Sensitive (S)** | Full names, emails, voice data, payment info, conversation content | Yes (AES-256 at rest) | High (delete immediately upon request) |
| **Internal (I)** | System logs, audit logs, analytics, aggregated metrics | Yes | Medium (follow retention schedule) |
| **Public (P)** | Company blog posts, help articles, public API docs | No | Low (may be archived indefinitely) |

---

## Appendix: Vendor Data Sharing

Maintain current vendor list in SUBPROCESSOR-TABLE.md with:
- Vendor name and service type
- Data types shared (minimize to essential fields only)
- Vendor's data retention policy
- Vendor's DPA status (signed/pending)
- Vendor's deletion capability (automatic, manual request, certification)
- Last deletion confirmation date

Example:
```
| Vendor | Data Shared | Retention | DPA Signed | Last Deletion Verified |
|--------|------------|-----------|-----------|----------------------|
| OpenAI | Conversation text (anonymized) | 30 days | Yes (2026-03-15) | 2026-03-20 |
| Stripe | Card last-4, amount, date | 7 years (PCI) | Yes (2025-01-10) | N/A (legal hold) |
| Twilio | Voice recording, transcript | 7 days | Pending | 2026-03-18 |
```
