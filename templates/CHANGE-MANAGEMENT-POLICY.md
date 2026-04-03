# Change Management Policy

**Company:** [YOUR COMPANY]
**Application:** [YOUR APP]
**Version:** 1.0
**Effective Date:** [DATE]
**Last Updated:** [DATE]
**Owner:** [YOUR NAME], Engineering Lead

---

## Team Size Adaptation

This template uses role names like "Engineering Lead" and "Security Lead" as placeholders. For solo founders, you fill all these roles yourself — simply use your own name. For small teams (2–5), assign roles based on who has the most relevant expertise. The controls are the same regardless of team size; only the assignment changes.

---

## Overview

This policy defines how changes to [YOUR APP] are planned, reviewed, tested, deployed, and documented. The policy is designed for solo developers and small teams, with a focus on safety, auditability, and rapid incident recovery.

<!-- CUSTOMIZE: Adjust approval tiers and review procedures based on team size and risk tolerance -->

---

## Change Categories & Approval Requirements

All changes must be categorized and follow the appropriate review/approval process before deployment.

### 1. Standard Changes (Low Risk)

**Definition:** Bug fixes, non-breaking feature additions, refactoring, documentation updates, dependency updates (non-breaking).

**Examples:**
- Fix typo in error message
- Update non-critical UI element
- Refactor internal function with same behavior
- Add new feature behind feature flag (disabled by default)
- Update minor dependency (patch version)
- Update text in static pages

**Approval Required:** Self-review only (solo developer) OR peer review if team exists

**Change Record:** Minimal (link to PR/commit)

**Testing Required:**
- ✓ Unit tests pass
- ✓ Integration tests pass (if applicable)
- ✓ Manual testing in staging environment
- ✓ No breaking database migrations
- ✓ No security/compliance impact

**Deployment Timeline:** Same day or next day after approval

**Procedure:**
1. Commit to feature branch with clear message: `[STANDARD] Add feature X / Fix bug Y`
2. If solo dev: self-review PR, ensure tests pass
3. If team: request 1 peer review (code + testing sign-off)
4. Deploy to staging, verify in staging environment
5. Deploy to production (can use automated CI/CD)
6. Monitor logs for 30 minutes post-deployment
7. Document in CHANGELOG.md with change type and date

---

### 2. Significant Changes (Medium Risk)

**Definition:** Major feature rollouts, database schema changes, API changes, critical dependency updates, third-party vendor integrations, security patches, configuration changes affecting multiple services.

**Examples:**
- New API endpoint or breaking API change
- Database migration (add/drop column, alter constraints)
- Integrate new payment processor or LLM vendor
- Update critical dependency (major version)
- Change authentication flow or security mechanism
- Deploy new service or infrastructure component
- Change data retention or deletion behavior
- Update customer-facing privacy/security settings

**Approval Required:**
- **Solo dev:** Self-review + document change plan + request stakeholder sign-off (even if same person, document it)
- **Small team:** Engineering Lead + 1 peer review + optional stakeholder approval (product/security/legal depending on change type)

**Change Record:** Detailed (see Change Request Template below)

**Testing Required:**
- ✓ All unit/integration tests pass
- ✓ Manual testing in staging (including rollback scenario)
- ✓ Database backup before migration
- ✓ API contract testing (if API change)
- ✓ Security/compliance review (if applicable)
- ✓ Performance impact assessment (if applicable)
- ✓ Data validation (if data model change)

**Deployment Timeline:** Requires 3 days advance planning/documentation; deployment after testing complete

**Procedure:**
1. Create Change Request (see template below)
2. Document in GitHub issue or CHANGE-LOG.md:
   - What is changing and why
   - Estimated impact (affected features, customer impact)
   - Rollback plan
   - Data migration details (if applicable)
   - Testing results
3. Notify stakeholders 2–3 days before deployment (product, legal, security if applicable)
4. Deploy to staging at least 1 day before production
5. Run full staging test suite + manual testing
6. Conduct dry-run rollback to verify procedure
7. Deploy to production with monitoring during deployment
8. Monitor for 1–2 hours post-deployment
9. Keep rollback plan on-standby for 24 hours
10. Document deployment completion and any issues in CHANGE-LOG.md

---

### 3. Emergency Changes (Critical Risk / Live Incident)

**Definition:** Security hotfixes, critical bugs affecting availability/data, urgent compliance fixes, incident mitigation.

**Examples:**
- Security vulnerability discovered in production
- Data corruption or loss detected
- Service outage caused by bug
- Urgent compliance violation (e.g., GDPR data breach mitigation)
- Attack in progress requiring immediate code change

**Approval Required:**
- **Immediate:** Deploy to fix issue; approval can be post-deployment
- **Post-incident:** Require stakeholder review and documentation within 24 hours

**Change Record:** Detailed incident log + post-incident review (see Incident Response section)

**Testing Required:**
- ✓ Quick sanity test in staging OR test on production with automated rollback ready
- ✓ Minimal testing to verify fix works and doesn't break other features
- ✓ Backup created before deployment
- ✓ Rollback plan documented

**Deployment Timeline:** Within 30 minutes to 2 hours (depending on severity)

**Procedure:**
1. **Incident Declared:** Create incident channel/issue, assign incident commander
2. **Rapid Fix:** Branch from main, implement fix, test quickly
3. **Deploy:** Deploy to production with extreme caution (perhaps gradual rollout if available)
4. **Monitor:** Active monitoring for 30 minutes post-deployment
5. **Rollback Ready:** Maintain rollback procedure on-standby
6. **Post-Incident (within 24 hours):**
   - Document what happened, why, and how it was fixed
   - Root cause analysis
   - Preventive measures (new tests, automation, architecture changes)
   - Update CHANGE-LOG.md with incident marker: `[EMERGENCY] Fix security issue / Fix critical bug`

---

## Change Request Template

Use this template for Significant and Emergency changes:

```markdown
# Change Request: [Title]

**Date Submitted:** [DATE]
**Change Type:** [Standard | Significant | Emergency]
**Affected Components:** [List: API, Database, UI, Auth, etc.]

## Description
[What is changing? Why? Business justification?]

## Scope & Impact
- **Affected Users/Features:** [Who/what is affected?]
- **Data Impact:** [Is data migrated/deleted/modified?]
- **Downtime Required:** [Yes/No, duration?]
- **API Changes:** [Breaking/non-breaking?]
- **Database Changes:** [Schema migrations?]

## Rollback Plan
[How do we revert this change if needed?]
- Rollback steps
- Estimated rollback time
- Data rollback procedure (if applicable)

## Testing Performed
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Staging environment testing complete
- [ ] Rollback tested in staging
- [ ] Performance impact assessed (if applicable)
- [ ] Security review completed (if applicable)

## Risk Assessment
- **Risk Level:** [Low | Medium | High]
- **Potential Issues:** [What could go wrong?]
- **Mitigation:** [How will we handle issues?]

## Approvals
| Role | Name | Sign-off Date | Status |
|------|------|---------------|--------|
| Developer | [YOUR NAME] | [DATE] | ✓ |
| Peer Review | [NAME] | [DATE] | ✓ |
| Lead / Stakeholder | [NAME] | [DATE] | ✓ |

## Deployment Details
- **Target Environment:** [Staging → Production]
- **Scheduled Date/Time:** [DATE/TIME]
- **Estimated Duration:** [30 min | 1 hour | etc.]
- **Monitoring Plan:** [Dashboard/alerts to watch post-deployment]

## Post-Deployment Verification
- [ ] Deployment successful
- [ ] Monitoring shows normal behavior
- [ ] No error rate spike
- [ ] Performance metrics stable
- [ ] Customer-facing features working
- [ ] Rollback plan stood down at [TIME]
```

---

## Detailed Procedures

### Code Review Checklist (All Changes)

Before any code is deployed:

- [ ] **Functionality:** Does the code do what it's supposed to do?
- [ ] **Tests:** Are new tests added? Do all tests pass?
- [ ] **Security:** No hardcoded secrets, SQL injection, or auth bypasses?
- [ ] **Performance:** Any N+1 queries, memory leaks, or slowdowns introduced?
- [ ] **Logging:** Sufficient logging for debugging/monitoring?
- [ ] **Documentation:** Code comments, README updates, API docs updated?
- [ ] **Dependencies:** New dependencies reviewed for security/license?
- [ ] **Breaking Changes:** Is this a breaking change? Documented?
- [ ] **Backwards Compatibility:** Do we support old API versions?
- [ ] **Error Handling:** Proper error handling and user-friendly messages?

---

### Staging Deployment Procedure

1. **Prepare:** Create fresh staging environment from latest production backup
2. **Deploy:** Run deployment script to staging
3. **Health Check:** Verify application health (health endpoint, basic functionality)
4. **Smoke Test:** Run critical user flows (login, core features, payment)
5. **Regression Test:** Run full test suite
6. **Performance Test:** Check query performance, response times
7. **Security Scan:** Run SAST/dependency security tools
8. **Rollback Dry-Run:** Practice rollback (restore old code/data)
9. **Sign-Off:** Document "staging approved" in change request

---

### Production Deployment Procedure

**Pre-Deployment Checklist:**
- [ ] Staging approval documented
- [ ] Backup of production database created
- [ ] All approval sign-offs collected
- [ ] Rollback plan verified
- [ ] Monitoring alerts configured
- [ ] On-call engineer standing by
- [ ] Deployment window announced to team/users (if applicable)

**Deployment Steps:**
1. Create release branch: `release/v[VERSION]`
2. Deploy to production (gradual rollout if available, e.g., 10% → 50% → 100%)
3. Run health check and basic functionality tests
4. Monitor error rate, latency, and resource usage
5. If all green after 15 minutes, proceed to full rollout
6. If issues detected, immediately rollback (see Rollback Procedure)

**Post-Deployment (Next 24 Hours):**
- [ ] Monitor error logs and alerts
- [ ] Monitor performance metrics
- [ ] Check for customer-reported issues
- [ ] Verify data integrity (if applicable)
- [ ] Document deployment completion

---

### Rollback Procedure

If production deployment fails:

1. **Decision:** Determine if rollback is necessary (usually yes for any critical issue)
2. **Communication:** Notify team of rollback decision
3. **Execute Rollback:**
   - Restore previous application version from last stable release
   - Restore database from backup (if data-altering change)
   - Verify rollback success (health checks, basic tests)
4. **Monitoring:** Monitor for 30 minutes post-rollback
5. **Investigation:** Root cause analysis; don't re-deploy until issue understood
6. **Communication:** Notify customers if applicable
7. **Documentation:** Document rollback in CHANGE-LOG.md with "ROLLED BACK" status

**Rollback Time Estimate:** [X minutes] (<!-- CUSTOMIZE: e.g., 5–10 minutes for code-only rollback, 30–60 minutes for database rollback -->)

---

### Database Migration Procedure

For schema changes (Significant Change):

1. **Backup:** Create full backup of production database
2. **Dry-Run:** Test migration on staging environment (from production backup)
3. **Rollback Plan:** Document how to undo migration (reverse SQL scripts)
4. **Testing:** Run data validation queries post-migration (e.g., row counts, constraints)
5. **Monitoring:** Watch for migration locks, performance issues during migration
6. **Communication:** Schedule migration during low-traffic window; notify users if downtime expected
7. **Verification:** Post-migration, run full test suite and spot-check data
8. **Documentation:** Document migration in code with version number and rationale

**Example Migration Tracking:**
```sql
-- Migration: V001__add_user_consent_column.sql
-- Author: [YOUR NAME]
-- Date: 2026-04-03
-- Status: ✓ Applied to production on 2026-04-03 14:30 UTC

ALTER TABLE users ADD COLUMN consent_marketing BOOLEAN DEFAULT FALSE;
ALTER TABLE users ADD COLUMN consent_timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP;

-- Rollback:
-- ALTER TABLE users DROP COLUMN consent_marketing;
-- ALTER TABLE users DROP COLUMN consent_timestamp;
```

---

### Feature Flag / Gradual Rollout

For new or risky features, use feature flags:

**Deploy Code (All Users, Disabled):**
```python
if FEATURE_FLAG_NEW_PAYMENT_PROCESSOR:
    # Use new payment processor
    payment_result = new_processor.charge(amount)
else:
    # Use current processor
    payment_result = current_processor.charge(amount)
```

**Rollout Stages:**
1. **Deploy with flag OFF:** All users see old behavior
2. **Enable for 1% → 10% → 50% → 100%:** Monitor error rates at each stage
3. **Monitor for 24–48 hours at each stage**
4. **Remove flag after stable:** Clean up code, remove old processor logic

---

## Monitoring & Alerting During Deployments

<!-- CUSTOMIZE: Adjust thresholds based on your application -->

**Critical Alerts (Page On-Call):**
- Error rate > 1% (deploy-time spike)
- API latency p99 > 5 seconds
- Database connection pool exhausted
- Disk space < 10%
- CPU > 90%

**Warning Alerts (Slack notification):**
- Error rate > 0.5%
- API latency p99 > 2 seconds
- Memory > 80%
- Database slow query rate > 10% of queries

**Post-Deployment Monitoring:**
- Monitor for 15–30 minutes (critical changes: 1–2 hours)
- Check error logs for any new error types
- Check performance metrics (latency, throughput)
- Verify no data inconsistencies
- Check third-party vendor health (if applicable)

---

## Documentation & Audit Trail

### CHANGELOG.md Format

```markdown
# Changelog

All notable changes to [YOUR APP] are documented here.

## [Unreleased]
- [STANDARD] Fix bug in conversation parsing
- [SIGNIFICANT] Add new voice API integration (staged rollout)

## [1.2.0] - 2026-04-03
- [STANDARD] Update UI styling for better readability
- [SIGNIFICANT] Migrate database to [YOUR DATABASE] v14.2
- [EMERGENCY] Patch XSS vulnerability in message sanitizer

## [1.1.0] - 2026-03-20
- [STANDARD] Add user preference for email notifications
- [SIGNIFICANT] Integrate Stripe payment processor

## [1.0.0] - 2026-01-15
- Initial release
```

### Git Commit Message Format

```
[TYPE] Subject line (50 chars max)

Body (72 chars per line, explain why, not what):
- What problem does this solve?
- Why this approach?
- Any breaking changes?

Fixes: #123 (GitHub issue number)
```

**Type:** `[STANDARD]`, `[SIGNIFICANT]`, `[EMERGENCY]`, `[DOCS]`, `[TEST]`

**Example:**
```
[SIGNIFICANT] Integrate OpenAI API for conversation generation

This change introduces OpenAI API integration for generating AI responses
in conversations. The feature is deployed with a feature flag (disabled by
default) and will be gradually rolled out to 1% of users initially.

Database migration required: users.ai_provider column added.
No breaking API changes.

Fixes: #456
```

---

## Solo Developer Self-Review Checklist

Since [YOUR APP] may be managed by a solo developer, use this checklist for self-review:

**Before Committing:**
- [ ] Does the change solve the intended problem?
- [ ] Are there any edge cases or error conditions I missed?
- [ ] Would a future developer understand this code?
- [ ] Is there any security risk I'm introducing?
- [ ] Are there performance implications?

**Before Pushing:**
- [ ] All tests pass locally?
- [ ] Did I add tests for new functionality?
- [ ] Is the commit message clear?
- [ ] Any debug code left behind?
- [ ] Any hardcoded values that should be config?

**Before Deploying to Staging:**
- [ ] Does the change match the PR description / issue description?
- [ ] Have I tested in staging environment?
- [ ] Does rollback plan make sense?
- [ ] Have I considered customer impact?

**Before Deploying to Production:**
- [ ] Has staging been tested for at least 1 hour?
- [ ] Any customer-facing changes documented (privacy policy, help docs)?
- [ ] Have I notified stakeholders of timing?
- [ ] Is monitoring configured for any new metrics?
- [ ] Do I have a clear rollback plan?

---

## Scheduled Deployment Windows

<!-- CUSTOMIZE: Set times based on your customer base and traffic patterns -->

**Preferred Deployment Windows:**
- Tuesday–Thursday, 2–4 PM UTC (off-peak hours)
- Avoid: Mondays (weekend issues), Fridays (post-incident risk)

**Emergency Deployments:**
- Can deploy anytime; just require faster testing and monitoring

**Customer Communication:**
- Planned significant changes: announce 3–5 days in advance
- Maintenance windows: announce 24 hours in advance
- Emergency changes: notify after deployment complete (within 1 hour)

---

## Compliance & Change Audits

### Change Audit Trail

Every change must be auditable:
- Git commit history (who, what, when)
- Pull request reviews (approval)
- Deployment logs (when deployed to prod)
- Change tracking spreadsheet (for non-dev changes)

**Audit Query Example:**
```bash
# Show all significant/emergency changes in past 3 months
git log --oneline --grep="\[SIGNIFICANT\]|\[EMERGENCY\]" --since="3 months ago"

# Show all production deployments
grep "deployed to production" deployment.log
```

### SOC 2 Compliance for Change Management

Change management is a SOC 2 Control (CC7: Change Management):

- ✓ All changes documented before deployment
- ✓ Testing evidence retained (test logs, screenshots)
- ✓ Approval audit trail (PR reviews, sign-offs)
- ✓ Deployment record (deployment logs, timestamps)
- ✓ Rollback procedure documented
- ✓ Emergency change procedures documented
- ✓ Change access restricted (only authorized deployments)

**Retention:** Keep change records and deployment logs for 1+ year for audit

---

## Annual Review & Updates

This policy should be reviewed annually and updated if:
- Change frequency increases
- Team size changes
- New tools adopted (CI/CD, monitoring, etc.)
- Incident post-mortems indicate policy gaps
- New compliance requirements emerge

**Review Schedule:**
- **Date:** [DATE] (annually)
- **Responsible:** [YOUR NAME], Engineering Lead

---

## Change Log

| Date | Change | Owner |
|------|--------|-------|
| [DATE] | Initial policy | [YOUR NAME] |
| [DATE] | Added feature flag procedure | [YOUR NAME] |

---

## Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Engineering Lead | [YOUR NAME] | _____________ | ________ |
| CEO / Founder | [YOUR NAME] | _____________ | ________ |
