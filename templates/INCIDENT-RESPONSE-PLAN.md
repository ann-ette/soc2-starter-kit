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
| **Sev 1 (Critical)** | Active data breach, system compromise, or user data exposure | Database breach, leaked credentials in use, unauthorized access to production | Immediate (within 1 hour) |
| **Sev 2 (High)** | Potential data exposure, significant vulnerability, or service outage | Secrets committed to public repo, critical CVE in production dependency, extended downtime | Within 4 hours |
| **Sev 3 (Medium)** | Security weakness, minor vulnerability, or suspicious activity | Failed intrusion attempt, moderate CVE, unusual API usage patterns | Within 24 hours |

### AI-Specific Incidents

An AI product has incident types a conventional plan never names. Classify them with the same severities.

<!-- CUSTOMIZE: Delete rows for AI features you don't ship. Name your actual providers in the third row. -->

| Incident | Example | Default Severity | First Containment Step |
|----------|---------|------------------|------------------------|
| **Harmful output to a user** | The model gives self-harm instructions, sexual content to a minor, dangerous advice, or presents itself as a clinician | Sev 1 if a user may be at risk; otherwise Sev 2 | Follow the published crisis protocol where it applies, then block the prompt path or roll back the model or prompt version that produced it |
| **Injection-driven data exposure** | A crafted message or retrieved document makes the model reveal another user's data or secrets in its instructions, or call a tool it should not | Sev 1 if another user's data left the system; otherwise Sev 2 | Disable the affected tool or retrieval source, rotate any exposed secret, preserve the conversation logs |
| **AI provider breach or terms change** | Your LLM, speech, voice or avatar vendor reports a breach, or changes its retention or training terms | Sev 1 if your users' data is in the breach scope; otherwise Sev 2 | Confirm what you sent the vendor and how long it kept it, switch to a fallback provider or disable the feature, and start the notification clock if personal data is in scope |
| **Model or prompt regression** | A provider model update or your own prompt change drops a safety behavior or the AI disclosure | Sev 2 | Roll back to the last known-good model and prompt version |

For every AI incident, preserve the full transcript and the exact model and prompt version that produced the output. A model response cannot be reproduced later without them, and they are the evidence both an auditor and a regulator will ask for.

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

<!-- CUSTOMIZE: Deadlines run from discovery and depend on where affected people live, not where you are. Check each state with affected residents; California, Colorado, New York and Washington, among others, require notice within 30 days. If you process biometric identifiers of Colorado residents, Colorado requires this plan to include a biometric breach protocol with consumer notice. -->

**Internal notification:**

- Document the incident in the incident log immediately upon detection
- Notify any contractors or team members with relevant access

**User notification (if personal data was exposed):**

| Regulation | Notification Deadline | Who to Notify |
|------------|----------------------|---------------|
| **GDPR** | Supervisory authority without undue delay and, where feasible, within 72 hours of becoming aware, unless the breach is unlikely to result in a risk; individuals without undue delay when the risk to them is high (not needed if, for example, the data was encrypted); a processor tells the controller without undue delay | Data Protection Authority + affected users where risk is high |
| **California (Civil Code 1798.82)** | Within 30 calendar days of discovery or notification, with delay allowed only for law enforcement or to determine scope and restore the system; sample notice to the Attorney General within 15 calendar days of notifying if more than 500 California residents | Affected California residents; Attorney General if more than 500 |
| **New York (Gen. Bus. Law 899-aa)** | Within 30 days after discovery | Affected New York residents and the state agencies the statute names; the Department of Financial Services only if you are a covered entity under 23 NYCRR 500.1 |
| **HIPAA** (if applicable) | Individuals without unreasonable delay and no later than 60 calendar days after discovery; HHS at the same time if 500 or more, otherwise in a log sent within 60 days after year end; media if more than 500 residents of a state; a business associate tells the covered entity within the same 60 days | Individuals + HHS + media (if applicable) |
| **FTC Health Breach Notification Rule** (non-HIPAA apps that are personal health record vendors) | Without unreasonable delay and no later than 60 calendar days after discovery; FTC at the same time if 500 or more, otherwise in a log within 60 days after year end; media if 500 or more residents of a state | Individuals + FTC + media |
| **Internal target** | Within 72 hours of confirming exposure, unless a shorter legal deadline applies | Affected users via email |

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

- Annually (at minimum), with a tabletop exercise: walk one scenario (a leaked key, an AI provider breach, a harmful-output report) through this plan from detection to notification, and record the date, the scenario, and every gap found. That record is the evidence for incident recovery plan testing under CC7.5
- After every Sev 1 or Sev 2 incident
- After major changes to the application architecture or vendor relationships

---

**Document History:**

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | [DATE] | [YOUR NAME] | Initial version |
