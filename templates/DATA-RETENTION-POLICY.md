# Data Retention Policy

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME], Privacy Lead

---

## Team Size Adaptation

This template uses role names like "Privacy Lead" as a placeholder. For solo founders, you fill all these roles yourself. Use your own name. For small teams (2–5), assign roles based on who handles privacy/compliance. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This policy defines retention periods and deletion procedures for all data types processed by [YOUR APP]. The policy is designed to meet the storage-limitation duties in the GDPR, the CCPA and similar laws, so customer data is retained only as long as necessary for the purposes it was collected for.

<!-- CUSTOMIZE: Adjust retention periods based on your business, legal, and regulatory requirements -->

---

## Data Retention Table

| Data Type | Description | Retention Period | Legal Basis | Deletion Method | Notes |
|-----------|-------------|-----------------|-------------|-----------------|-------|
| **User Account Data** | Name, email, password hash, account creation date, last login | Until account deletion, minimum 30 days post-deletion | Contract (service provision), Consent | Encrypted deletion from [YOUR DATABASE], backups aged out | See Account Deletion SOP below. PII retained if user requests export. |
| **Conversation History / Chat Data** | User messages, AI responses, timestamps, metadata | [X] months from last activity, or user deletion request | Contract (providing the conversation); consent for any use beyond that, such as training | Secure deletion from database and backups | Users can request deletion anytime via DSAR. AI training: never without explicit consent. |
| **Voice / Audio Recordings** | Raw audio files from voice API, transcriptions | [X] days to [X] weeks (balance: enough for support, minimal PII retention) | Consent, Legitimate interest (customer support) | Automatic deletion after retention period; encryption at rest | Must comply with voice API vendor retention policy (see SUBPROCESSOR-TABLE). Under the GDPR, voice is special-category data when processed to uniquely identify someone. Illinois and Texas cover voiceprints; neither lists recordings. Connecticut excludes audio recordings unless data from them is generated to identify someone. Washington's biometric law excludes audio recordings and data generated from them. Colorado excludes audio recordings from "biometric data" unless used to identify someone, but a voiceprint, or other data that can be processed to uniquely identify someone, is a "biometric identifier", with notice and deletion duties at any volume. California and Washington's health-data law count a recording from which a voiceprint can be extracted. Recordings of children under 13 are personal information under COPPA. |
| **Biometric Data** | Voice prints, facial recognition data (if collected) | Earliest of purpose met, consent withdrawn, [X] days, or the statutory limit in Notes | Explicit Consent (high sensitivity) | Irreversible deletion via vendor; cannot be re-derived | Never retained longer than necessary. Illinois BIPA: a public retention schedule, destruction when the purpose is met or within 3 years of the user's last interaction, whichever comes first. Texas CUBI, for identifiers captured for a commercial purpose: destroy within a reasonable time and no later than one year after the purpose expires; since 2026-01-01 Texas exempts biometric identifiers used to develop or offer AI systems unless the system is used to identify people. Colorado (any volume, since 2025-07-01): a public written policy and deletion by the earliest of purpose met, 24 months after last interaction, or 45 days (extendable by 45) after an annual review finds it unnecessary. Washington (RCW 19.375.020(4)(b)), for identifiers enrolled for a commercial purpose: no longer than reasonably necessary. |
| **Payment Data** | Credit card last-4 digits, billing address, payment method type | Until account deletion or end of contract | Contract | Tokenized via payment processor; never stored in [YOUR DATABASE] | Full card data stays with the payment processor, which keeps most of PCI DSS out of your scope; you still complete the processor's self-assessment questionnaire. |
| **Transaction / Billing Records** | Invoice numbers, amounts, dates, payment status | [PERIOD SET BY TAX AND ACCOUNTING LAW] (varies by country: UK companies keep accounting records for 6 years; in the US the IRS asks for 3 years in most cases and 7 for a bad-debt or worthless-securities claim) | Legal obligation (tax and accounting law) | Archived to restricted, encrypted storage; deleted when the period ends | Retained because the law requires it, so a deletion request does not reach these records. |
| **System & Application Logs** | API request logs, error logs, access logs, performance metrics | 90 days (hot), 1 year archive | Legitimate interest (security, troubleshooting) | Automated purge from hot storage; archive to cold storage | May contain PII (email addresses, user IDs). Anonymize or aggregate after 90 days where possible. |
| **Audit Logs** | Admin actions, permission changes, security events, failed access attempts | 1 year minimum (a common audit expectation; SOC 2 itself sets no fixed period) | Legitimate interest (security, audit) | Archived to immutable, encrypted cold storage | Critical for incident investigation. Longer retention for high-risk actions (e.g., data export). |
| **Backup Data** | Full database snapshots, application state, configuration | 30 days (recent), 1 year incremental | Legitimate interest (disaster recovery) | Delete from backup systems after retention; verify deletion | Encryption-in-transit and at rest required. Test restoration quarterly. |
| **Cached API Responses** | Responses from third-party APIs (LLM, translation, etc.) | [X] days (depends on API provider terms) | Consent, Legitimate interest (performance) | Automatic cache expiration; no manual deletion needed | Check vendor terms (some APIs prohibit caching). Do not cache PII. |
| **Analytics / Aggregated Data** | User behavior, feature usage, aggregated metrics | [PERIOD] (match your analytics tool's retention setting) | Consent where cookies or device storage are used; otherwise legitimate interest | Automated deletion of data past the period; retain only aggregated summaries | Truly anonymized aggregates fall outside the GDPR (Recital 26). Pseudonymized data, such as events keyed to a user or device ID, is still personal data. |
| **Support Tickets / Help Center Logs** | Support conversations, help requests, resolution notes | 1 year post-closure, or user deletion request | Legitimate interest (customer support, legal protection) | Delete from ticketing system and backups after 1 year | May contain customer PII. Anonymize summaries before long-term archival. |
| **Email Communications** | Transactional emails, marketing emails, password reset links, security alerts | Transactional: until account deletion; Marketing: until unsubscribe | Consent (marketing), Contract (transactional) | Deleted from email system and backups per user retention above | Keep a suppression list for as long as you send marketing email, so an unsubscribed address is never mailed again (CAN-SPAM requires opt-outs honored within 10 business days). |
| **IP Addresses / Device Identifiers** | User IP, device ID, browser fingerprint, geolocation | 90 days (rolling window) | Legitimate interest (security, fraud detection) | Anonymized or aggregated after 90 days | Used for abuse detection and access logs. Anonymization acceptable alternative to deletion. |
| **Third-Party Vendor Data** | Data shared with LLM provider, payment processor, analytics platform | Per vendor agreement and DPA; minimum: as long as service active | Contract (vendor terms), DPA requirements | Vendor responsible for deletion; [YOUR COMPANY] audit yearly | Refer to SUBPROCESSOR-TABLE for vendor-specific terms. Right to audit vendor deletion. |
| **Cookies / Web Tracking Data** | Session cookies, analytics cookies, ad cookies, consent preferences | Session (deleted on logout) or [X] days per cookie policy | Consent (per cookie consent banner) | Automatic deletion per expiration; user can clear via privacy controls | Document cookie types in Privacy Policy. Honor Global Privacy Control (GPC) signals as an opt-out of sale or sharing, which California requires of businesses that sell or share, as do other states including Connecticut and Oregon. |
| **Database Archives / Point-in-Time Backups** | Snapshots for disaster recovery, compliance audits | 30 days recent, 90 days incremental, 1 year full snapshots | Legitimate interest (disaster recovery, audit trail) | Delete via database snapshot schedule; verify immutable archive only | Test restoration to confirm backups are usable. Consider separate encryption key. |
| **User Consent Records** | Consent choices (marketing, analytics, voice training), consent timestamps, withdrawal history | Until withdrawal or account deletion; 3 years post-withdrawal for record-keeping | Legal obligation to be able to demonstrate consent (GDPR Article 7(1)) | Archived if account deleted; retained if withdrawal | No law found sets the 3-year period; it is your choice. Keep only the record of the choice. California separately requires records of privacy requests and your responses for 24 months (11 CCR 7101(a)). |
| **Security Incident Records** | Breach investigation data, forensics, incident reports, remediation actions | [PERIOD] | Legal requirement (regulatory, litigation hold) | Archived to immutable storage; never deleted during hold period | The GDPR and UK GDPR (Article 33(5)) require a record of every breach but set no period; Canada requires 24 months (SOR/2018-64 s.6); HIPAA covered entities and business associates keep required security documentation 6 years (45 CFR 164.316(b)(2)(i)). |
| **Privacy Risk Assessments** (CCPA businesses that process sensitive personal information, such as voiceprints used to identify) | Risk assessments and their updates | As long as the processing continues or 5 years after the assessment is completed, whichever is later | Legal obligation (11 CCR 7155(c)) | Archive, then delete | Assess before starting the processing; processing that began before 2026 must be assessed by 2027-12-31. |
| **User Settings & Preferences** | Notification settings, language, timezone, UI preferences, feature flags | Until account deletion | Contract (service personalization) | Deleted with account data | Non-sensitive; may be anonymized in aggregate analytics. |
| **Embeddings / Vector Index** | Vectors derived from user content for retrieval or memory | Same as the content they were derived from | Same as source content | Deleted with the source content; deletion job covers the vector store | Regulators generally treat embeddings of personal content as personal data. The most common place a deletion promise quietly fails. |
| **Conversation Memory and Summaries** | Model-written summaries, extracted facts, long-term memory about a user | Same as conversation history | Same as conversation history | Deleted with the account and on request | Derived data the user may not know exists; disclose it in the privacy policy. |
| **Prompt and Completion Logs (Yours)** | Full prompts and responses logged for debugging or quality | [X] days | Legitimate interest (debugging, safety) | Automated purge | Often contain everything the user said. Keep the window short, or log metadata only. |
| **Prompts and Outputs Held by AI Providers** | Content your AI vendors retain on their side | Per vendor terms (e.g. up to 30 days for abuse monitoring, or zero with zero data retention enabled) | Contract (DPA) | Vendor deletes per its terms; record the terms in SUBPROCESSOR-TABLE | Training opt-out and retention are separate controls; record both. |
| **Evaluation and Safety Test Sets** | Conversations kept to test prompts and models before release | Until replaced | Legitimate interest (safety testing) | Reviewed each release; removed when replaced | Build these from synthetic or consented conversations rather than raw user data. |
| **Children's Personal Information** (only if your service is directed to children under 13, in whole or part) | Data collected from a child | Only as long as reasonably necessary for the purpose collected; never indefinitely | Legal obligation (COPPA, 16 CFR 312.10; compliance date 2026-04-22) | Delete with measures that prevent unauthorized access during deletion | Publish this written policy (purposes, business need, deletion timeframe) in your children's privacy notice. Audio of a child's voice collected only to answer a request is deleted immediately after. |

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
- Transaction records retained for the period tax and accounting law requires
- Audit logs retained for 1 year (security requirement)
- User consent records retained for [3 years] post-deletion (proof of consent; no law sets the period)

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
- One full snapshot per month stored in an S3 bucket with Object Lock in compliance mode (Object Lock requires versioning to be enabled)
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
| **Legal/Tax** | [PERIOD SET BY LAW] | [PERIOD SET BY LAW] | Tax and accounting law in each country you operate in |
| **Security/Audit** | 1 year | [PERIOD] | Incident investigation, audit sampling (SOC 2 sets no fixed period) |
| **Backup/Disaster Recovery** | 30 days | 1 year | Business continuity, compliance archival |
| **Analytics** | [PERIOD] | [PERIOD] | Product insights; match your analytics tool's retention setting |
| **Marketing/Consent** | Until unsubscribe | Suppression list: as long as you send marketing email. Consent records: [3 years] after withdrawal | CAN-SPAM (opt-outs honored within 10 business days, never mailed again); GDPR Article 7(1) proof of consent, no period set |
| **Voice recordings** | None | [X] days | Minimize; keep only what support needs |
| **Biometric (voiceprints, face templates)** | None | Earliest of purpose met or consent withdrawn, capped at 3 years after last interaction (Illinois), 24 months after last interaction (Colorado) and 1 year after the purpose ends (Texas) | BIPA 15(a), CUBI 503.001, Colorado HB24-1130 |

---

## Legal Basis for Retention

| Basis | Data Types | Retention Justification |
|-------|-----------|------------------------|
| **Contractual Obligation** | User account, conversation history, billing, support tickets | Service provision, payment processing, customer support |
| **Legal Obligation** | Billing records, consent records where a law requires proof | Tax and accounting law; GDPR Article 6(1)(c) covers obligations set by law, which a SOC 2 audit is not |
| **Legitimate Interest** | System and audit logs, device identifiers, fraud signals | Security, fraud detection, audit, performance optimization |
| **Consent** | Voice recordings, biometric data, marketing emails, analytics cookies | User has explicitly consented; can be withdrawn anytime |

---

## User Rights & Deletion Requests

### Data Subject Access Request (DSAR)

User has the right to request:
- Copy of all personal data retained about them
- Proof of retention basis
- The recipients who received or will receive their data, named individually (CJEU C-154/21), or by category where naming them is impossible or the request is manifestly unfounded or excessive (GDPR Article 12(5))
- Details on automated decision-making (if any)

**Response Timeline:** Under the GDPR, one month from receipt, extendable by two further months for complex or numerous requests (tell the user within the first month). Under the CCPA, 45 days, extendable once by 45 more. Use the shortest deadline that applies to the requester.

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

**Response Timeline:** Same as access requests above: one month under the GDPR (extendable by two months), 45 days under the CCPA.

**Process:**
1. User email [YOUR EMAIL] with "Deletion Request"
2. Confirm user identity
3. Execute account deletion procedure (see above)
4. Confirm completion to the user within the applicable deadline

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
5. Deliver within one month (GDPR)

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
| [LLM PROVIDER] | Conversation text | [PROVIDER DEFAULT, e.g. up to 30 days for abuse monitoring] | Yes ([DATE]) | [DATE] |
| [PAYMENT PROCESSOR] | Card last-4, amount, date | [PER PROCESSOR TERMS AND TAX LAW] | Yes ([DATE]) | N/A (legal obligation) |
| [VOICE PROVIDER] | Voice recording, transcript | [X] days | Pending | [DATE] |
```
