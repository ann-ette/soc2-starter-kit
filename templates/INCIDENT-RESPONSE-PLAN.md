# Incident Response Plan

**[YOUR COMPANY]**
**Version:** 1.0
**Effective Date:** [DATE]
**Owner:** [YOUR NAME / ROLE]

---

## 1. Purpose and Scope

This plan establishes procedures for identifying, responding to, and recovering from security incidents affecting [YOUR APP] and its users. It applies to all systems, data, and third-party services operated by [YOUR COMPANY].

### Systems in Scope

<!-- CUSTOMIZE: List your actual systems -->

- **Application server** ([YOUR CLOUD PROVIDER])
- **Database** ([YOUR DATABASE])
- **Third-party integrations** (list your vendors: e.g., voice API, LLM provider, payment processor, etc.)
- **Source code repository** (GitHub)
- **Domain and DNS** (your registrar/provider)

## 2. Incident Classification

| Severity | Description | Examples | Response Time |
|----------|-------------|----------|---------------|
| **Sev 1 — Critical** | Active data breach, system compromise, or user data exposure | Database breach, leaked credentials in use, unauthorized access to production | Immediate (within 1 hour) |
| **Sev 2 — High** | Potential data exposure, significant vulnerability, or service outage | Secrets committed to public repo, critical CVE in production dependency, extended downtime | Within 4 hours |
| **Sev 3 — Medium** | Security weakness, minor vulnerability, or suspicious activity | Failed intrusion attempt, moderate CVE, unusual API usage patterns | Within 24 hours |

## 3. Response Phases

### Phase 1: Detection

Incidents may be detected through:

- GitHub Actions security scan alerts (secret detection, dependency vulnerabilities)
- CodeQL static analysis findings
- User reports (via support email)
- Third-party vendor security notifications
- Manual review during weekly compliance report review
- Error monitoring and application logs

### Phase 2: Containment

**Immediate containment (within 1 hour of Sev 1 detection):**

1. Identify the scope: What data, systems, or users are affected?
2. Isolate the affected system if possible (revoke compromised credentials, disable affected endpoints)
3. Preserve evidence (logs, screenshots, database snapshots) before taking corrective action
4. Do NOT destroy logs or evidence

**Short-term containment:**

- Rotate all potentially compromised credentials
- If a secret was leaked: revoke immediately, generate new credentials, update all systems
- If unauthorized access occurred: terminate active sessions, force password resets for affected accounts
- If a vendor is compromised: disable the integration pending investigation

### Phase 3: Eradication

1. Identify the root cause (how did the incident occur?)
2. Remove the vulnerability or close the attack vector
3. Verify the fix (confirm the issue cannot recur through the same path)
4. Scan for indicators of compromise in related systems

### Phase 4: Recovery

1. Restore affected systems from known-good backups if necessary
2. Re-enable disabled services or integrations after verification
3. Monitor closely for 48–72 hours post-recovery for signs of recurrence
4. Confirm normal operation with functional testing

### Phase 5: Communication and Notification

<!-- CUSTOMIZE: Adjust notification timelines based on your applicable regulations -->

**Internal notification:**

- Document the incident in the incident log immediately upon detection
- Notify any contractors or team members with relevant access

**User notification (if personal data was exposed):**

| Regulation | Notification Deadline | Who to Notify |
|------------|----------------------|---------------|
| **GDPR** | 72 hours to supervisory authority; without undue delay to affected individuals | Data Protection Authority + affected users |
| **CCPA** | Without unreasonable delay | Affected California residents |
| **HIPAA** (if applicable) | 60 days to affected individuals; HHS notification; media if 500+ affected | Individuals + HHS + media (if applicable) |
| **General best practice** | Within 72 hours | Affected users via email |

**Notification content should include:**

- What happened (in plain language)
- What data was affected
- What you've done to address it
- What users should do (change passwords, monitor accounts, etc.)
- How to contact you with questions

### Phase 6: Post-Incident Review

Within 7 days of incident resolution:

1. Write an incident report documenting timeline, root cause, impact, and response
2. Identify what worked well and what needs improvement
3. Update this plan, security controls, or monitoring based on lessons learned
4. Add any new risks to the Risk Register
5. Archive the incident report as compliance evidence

## 4. Incident Log Template

| Field | Value |
|-------|-------|
| **Incident ID** | INC-[YYYY]-[NNN] |
| **Date Detected** | |
| **Severity** | Sev 1 / Sev 2 / Sev 3 |
| **Description** | |
| **Systems Affected** | |
| **Data Affected** | |
| **Users Affected** | |
| **Detection Method** | |
| **Containment Actions** | |
| **Root Cause** | |
| **Resolution** | |
| **Notification Sent** | Yes / No / N/A |
| **Date Resolved** | |
| **Post-Incident Review Date** | |
| **Lessons Learned** | |

## 5. Vendor Incident Contacts

<!-- CUSTOMIZE: Fill in actual contact details for your vendors -->

| Vendor | Contact | Status Page | SLA |
|--------|---------|-------------|-----|
| [YOUR CLOUD PROVIDER] | [support email] | [status page URL] | [response SLA] |
| [YOUR DATABASE] | [support email] | [status page URL] | [response SLA] |
| [Vendor 3] | [support email] | [status page URL] | [response SLA] |
| [Vendor 4] | [support email] | [status page URL] | [response SLA] |

## 6. Plan Review

This plan is reviewed and tested:

- Annually (at minimum)
- After every Sev 1 or Sev 2 incident
- After major changes to the application architecture or vendor relationships

---

**Document History:**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [DATE] | [YOUR NAME] | Initial version |
