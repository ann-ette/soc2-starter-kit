# SOC 2 Starter Kit for AI-Native Products

**Built for products handling voice data, behavioral analytics, generative AI, and multi-vendor data pipelines**

---

## What This Is

This is a comprehensive, production-ready collection of SOC 2 compliance templates specifically designed for solo founders and small teams building AI-native products. Unlike generic SOC 2 kits on GitHub (which assume standard SaaS on AWS with Stripe and Auth0), this kit is purpose-built for the reality of modern AI applications:

- **Voice and biometric data** processing (voice APIs, facial recognition, speaker ID)
- **Generative AI pipelines** (LLM APIs, fine-tuning, prompt injection risks)
- **Multi-vendor architectures** (10-15 vendors processing customer data, each a potential risk)
- **Solo founder workflow** (you fill every role; no HR, no compliance team)

**Open-sourced by [Lantern Works](https://lanternworks.dev)**, makers of [HistorAI](https://apps.apple.com/app/historai). MIT License.

---

## Who This Is For

**Perfect fit:**
- Solo founder running an AI/voice product with customers
- 2-5 person team with no dedicated compliance role
- Bootstrap or pre-Series A (can't afford $50K consulting fee)
- Building something that handles user data: conversations, voice, biometrics, behavioral data
- Want to move fast but build compliance *right*, not retrofit it

**Still a good fit, even if:**
- **You're pre-launch** — building with compliance in mind from day one is dramatically cheaper than retrofitting it later. Your architecture decisions, vendor choices, and data flows are easier to get right now than to fix after 10,000 users
- **You're B2C today** — enterprise, education, and healthcare partnerships come faster than you expect, and "SOC 2 controls implemented" opens doors that "we'll get to it" doesn't
- **You're building on a standard SaaS stack** — this kit still applies, though Vanta/Drata may be worth evaluating once you're ready for the audit itself

**This kit is honest:** It won't give you SOC 2 certification. Only an external auditor can do that. But it gives you 80% of the work done before you hire an auditor, saving $20K–$80K in consulting fees.

---

## What's Inside

**9 production-ready templates** (9,000+ lines):

1. **RISK-REGISTER.md** — 15+ risks specific to AI apps (prompt injection, voice data leakage, multi-vendor pipelines) with worked examples
2. **DATA-RETENTION-POLICY.md** — Retention schedules for 18+ data types with GDPR/CCPA deletion procedures
3. **CHANGE-MANAGEMENT-POLICY.md** — Deployment safety (standard/significant/emergency change tiers, rollback)
4. **SUBPROCESSOR-TABLE.md** — Vendor inventory, SOC 2 tracking, DPA status (critical for multi-vendor apps)
5. **VENDOR-ASSESSMENT.md** — 70+ security questions for evaluating new AI vendors
6. **SECRETS-AUDIT-CHECKLIST.md** — Git audit, secret rotation, automated scanning
7. **SOC2-CONTROL-MAPPING.md** — Maps your controls to all 9 SOC 2 Common Criteria (CC1-CC9) + Privacy/Confidentiality
8. **PRIVACY-POLICY-TEMPLATE.md** — GDPR/CCPA/App Store compliant; includes voice/biometric sections
9. **SECURITY-PAGE-TEMPLATE.md** — Public-facing trust/security page

Plus:
- **SOC2-GUIDE.md** — Full landscape: costs ($0 DIY vs. $180K full-service), what you get, honest trade-offs
- **COMPLIANCE-TRACKER-TEMPLATE.md** — Spreadsheet to track remediation + evidence
- **GitHub Actions workflows** — Automated secret scanning, dependency audits, static analysis

---

## Start Here: The Quick Path

**If you're a solo founder with 10 hours to invest:**

1. **Read** [SOC2-GUIDE.md](SOC2-GUIDE.md) (30 min) — Understand the landscape and whether you actually need this
2. **Skim** [RISK-REGISTER.md](templates/RISK-REGISTER.md) (20 min) — See which risks apply to your app
3. **Customize & save** all 9 templates in a folder (2 hours):
   - Find/replace `[YOUR COMPANY]`, `[YOUR APP]`, etc.
   - Read the `<!-- CUSTOMIZE: -->` comments
   - Fill in placeholders for your stack (database, cloud provider, vendors)
4. **Focus your effort** (7+ hours):
   - **SUBPROCESSOR-TABLE.md** — List every vendor; get their SOC 2 reports; sign DPAs
   - **DATA-RETENTION-POLICY.md** — Implement the deletion procedures (this is real code work)
   - **RISK-REGISTER.md** — Document mitigations for high-risk items
   - **PRIVACY-POLICY-TEMPLATE.md** — Publish on your website and App Store
5. **Gather evidence** as you implement (ongoing):
   - Save screenshots of security configs
   - Keep DPA signatures
   - Document access reviews
   - Log vendor assessments

**Timeline: 2-4 weeks part-time, 1-2 weeks full-time**

---

## Document Interdependencies

Not all templates are created equal. Some depend on others:

| Template | Standalone? | Depends On | Effort |
|----------|---|---|---|
| RISK-REGISTER.md | Yes | None | 1 day |
| SOC2-CONTROL-MAPPING.md | Yes | None | 2 days |
| PRIVACY-POLICY-TEMPLATE.md | Yes | None | 2 hours (customize) |
| SUBPROCESSOR-TABLE.md | Mostly | VENDOR-ASSESSMENT.md | 2-3 days (vendor outreach) |
| DATA-RETENTION-POLICY.md | Yes | None | 1 day (planning) + dev time |
| CHANGE-MANAGEMENT-POLICY.md | Yes | None | 1 day |
| VENDOR-ASSESSMENT.md | Yes | None | 1 day (template creation) |
| SECRETS-AUDIT-CHECKLIST.md | Yes | None | 1 day (tooling setup) |
| SECURITY-PAGE-TEMPLATE.md | Yes | None | 1 hour (copywriting) |

**Recommended order:**
1. Start with RISK-REGISTER and SOC2-CONTROL-MAPPING (understand your risks)
2. Do VENDOR-ASSESSMENT + SUBPROCESSOR-TABLE (critical: know your vendors)
3. Then PRIVACY-POLICY-TEMPLATE, DATA-RETENTION-POLICY (user-facing)
4. Then CHANGE-MANAGEMENT-POLICY, SECRETS-AUDIT-CHECKLIST (engineering practices)
5. Finally SECURITY-PAGE-TEMPLATE, SOC2-CONTROL-MAPPING refinement (trust-building)

---

## Adapting for Your Team Size

**Solo Founder:**
- You fill every role: Security Lead, Engineering Lead, Product, CEO
- Each template has a "Team Size Adaptation" note explaining role placeholders
- When templates ask for sign-offs (e.g., "Security Lead and Engineering Lead approved"), you sign both lines
- This is intentional — documenting that you've reviewed and accepted responsibility for each control

**2-5 Person Team:**
- Assign roles by expertise: Who knows infrastructure best? Who handles customer security questions?
- The person closest to each domain takes responsibility, but everyone reviews
- You don't need dedicated roles; you're just documenting "who's responsible for what"

**10+ Person Team:**
- Consider graduating to Vanta/Drata (their $15K/year platform saves more time at scale)
- Or hire a part-time compliance person (4-8 hours/week) to maintain these docs

---

## File Structure

```
soc2-starter-kit/
├── README.md                    ← Start here (this file)
├── SOC2-GUIDE.md                ← Full landscape: costs, benefits, trade-offs
├── LICENSE                      ← MIT License
├── .gitignore
├── .github/
│   └── workflows/
│       ├── security-scan.yml              ← Secret + dep scan (every push)
│       ├── weekly-compliance-report.yml   ← Weekly evidence report (Monday 9am UTC)
│       └── codeql-analysis.yml            ← Static analysis for JS/TS + Python
└── templates/
    ├── INFORMATION-SECURITY-POLICY.md     ← Core security policy (NIST SP 800-53)
    ├── INCIDENT-RESPONSE-PLAN.md          ← Severity classification + response procedures
    ├── RISK-REGISTER.md                   ← Risk matrix + worked AI-specific example
    ├── DATA-RETENTION-POLICY.md           ← Retention periods by data type
    ├── CHANGE-MANAGEMENT-POLICY.md        ← Standard/significant/emergency changes
    ├── SUBPROCESSOR-TABLE.md              ← Vendor inventory + DPA tracking
    ├── VENDOR-ASSESSMENT.md               ← Security questionnaire for new vendors
    ├── SECRETS-AUDIT-CHECKLIST.md         ← Secrets audit for your codebase
    ├── SOC2-CONTROL-MAPPING.md            ← Controls → SOC 2 Trust Service Criteria
    ├── COMPLIANCE-TRACKER-TEMPLATE.md     ← Spreadsheet for evidence + remediation
    ├── PRIVACY-POLICY-TEMPLATE.md         ← Privacy policy (App Store + GDPR/CCPA)
    └── SECURITY-PAGE-TEMPLATE.md          ← Trust/security page for your website
```

---

## How to Use These Templates

### Step 1: Customize for Your Organization

1. **Fork this repository** or copy the templates to your internal compliance folder
2. **Find and Replace** all placeholders:
   - `[YOUR COMPANY]` → Your company name
   - `[YOUR APP]` → Your product name
   - `[YOUR DATABASE]` → Your database system (PostgreSQL, MySQL, etc.)
   - `[YOUR CLOUD PROVIDER]` → Your hosting provider (AWS, GCP, Azure)
   - `[YOUR EMAIL]` → Your contact email
   - `[DATE]` → Current date
3. **Review inline comments** marked with `<!-- CUSTOMIZE: -->`
   - These indicate sections you should customize for your specific architecture
   - Adjust retention periods, threshold values, approval workflows based on your needs

### Step 2: Implement Controls

1. Use **RISK-REGISTER.md** to identify your top risks
2. Use **SOC2-CONTROL-MAPPING.md** to map risks to SOC 2 controls
3. Implement controls using other templates as reference:
   - **DATA-RETENTION-POLICY.md** → Set up data deletion automation
   - **CHANGE-MANAGEMENT-POLICY.md** → Establish deployment procedures
   - **SECRETS-AUDIT-CHECKLIST.md** → Secure your codebase
   - **SUBPROCESSOR-TABLE.md** → Assess and document vendors
   - **VENDOR-ASSESSMENT.md** → Evaluate new integrations
   - **PRIVACY-POLICY-TEMPLATE.md** → Publish privacy terms
   - **SECURITY-PAGE-TEMPLATE.md** → Communicate security to customers

### Step 3: Gather Evidence

- Run through **SECRETS-AUDIT-CHECKLIST.md** to verify no secrets leaked
- Collect change logs, deployment records, and audit logs
- Document vendor assessments and DPA signatures
- Maintain records of training, reviews, and incidents

### Step 4: Prepare for Audit

- Use **SOC2-CONTROL-MAPPING.md** to verify all controls documented
- Review **RISK-REGISTER.md** for remediation completion
- Verify **SUBPROCESSOR-TABLE.md** DPAs are signed
- Ensure **PRIVACY-POLICY-TEMPLATE.md** is published and accessible

---

## Implementation Timeline

**Recommended schedule (spreads over 2-4 weeks):**

### Week 1-2: Documentation
- [ ] Customize all templates for your organization
- [ ] Review and refine customizations
- [ ] Create internal compliance document library

### Week 3-4: Risk Assessment
- [ ] Complete RISK-REGISTER.md (15+ risks identified)
- [ ] Map risks to SOC 2 controls (SOC2-CONTROL-MAPPING.md)
- [ ] Set remediation timelines for high-risk items

### Week 5-6: Vendor Audit
- [ ] Complete VENDOR-ASSESSMENT.md for each vendor
- [ ] Review/obtain SOC 2 reports from vendors
- [ ] Negotiate and sign DPAs (SUBPROCESSOR-TABLE.md)

### Week 7-8: Security Implementation
- [ ] Run SECRETS-AUDIT-CHECKLIST.md on codebase
- [ ] Implement CHANGE-MANAGEMENT-POLICY.md
- [ ] Set up DATA-RETENTION-POLICY.md automation (backups, deletion, retention)

### Week 9-10: Compliance & Privacy
- [ ] Publish PRIVACY-POLICY-TEMPLATE.md on website
- [ ] Publish SECURITY-PAGE-TEMPLATE.md to build trust
- [ ] Train yourself on security policies

### Week 11-12: Audit Preparation
- [ ] Gather 6+ months of evidence (logs, reviews, audits)
- [ ] Verify all controls documented in SOC2-CONTROL-MAPPING.md
- [ ] Engage external auditor for SOC 2 Type II audit (if pursuing certification)

---

## Important Notes

**These templates are provided as examples and should be customized for your jurisdiction:**
- Consult legal counsel before publishing Privacy Policy and Terms of Service
- Ensure compliance with GDPR, CCPA, HIPAA, and other applicable laws
- Update for your specific data handling, vendor agreements, and business practices
- Different industries (healthcare, finance, education) may have additional requirements

**What you're building:**
- A baseline of controls and documentation
- Evidence that you're taking security seriously
- A foundation for SOC 2 Type II audit (or for customer security due diligence)
- A reference for hiring and onboarding (when you grow)

**What you're not building:**
- A substitute for professional legal review
- A guarantee of SOC 2 certification (only an external auditor issues that)
- A substitute for ongoing security work (this is a starting point, not a set-it-and-forget-it)

---

## Template Statistics

- **Total Lines of Content:** 9,000+
- **Number of Templates:** 9 (plus guides, workflows, tracker)
- **Number of Customizable Placeholders:** 150+
- **Documented Controls:** 60+
- **Risk Examples:** 15+
- **Vendor Examples:** 10+
- **Assessment Questions:** 70+
- **Data Types Covered:** 18+

---

## Support & Maintenance

These templates are designed to be living documents. Update them:
- **Quarterly:** Risk assessment and control review
- **Semi-annually:** Policy and procedure updates
- **Annually:** Full SOC 2 audit preparation and renewal
- **As-needed:** New vendor integrations, regulatory changes, lessons learned from incidents

---

## Quick Reference: Key Controls for AI Apps

**Prompt Injection:**
→ Input validation, system prompt hardening, output filtering, rate limiting
→ See: RISK-REGISTER.md (RISK-002)

**Voice/Biometric Data:**
→ Strict consent, separate encryption, auto-delete, no training use without consent
→ See: RISK-REGISTER.md (RISK-004), PRIVACY-POLICY-TEMPLATE.md

**Multi-Vendor Pipelines:**
→ Vendor assessment, SOC 2 verification, DPA, data minimization, contingency planning
→ See: SUBPROCESSOR-TABLE.md, VENDOR-ASSESSMENT.md

**Data Retention & Deletion:**
→ Retention schedule by data type, automated deletion, GDPR/CCPA compliance
→ See: DATA-RETENTION-POLICY.md

**Access Control:**
→ MFA, least privilege, monthly access reviews, offboarding checklist
→ See: RISK-REGISTER.md (RISK-008)

---

## Credits

**Open-sourced by [Lantern Works](https://lanternworks.dev)** — makers of [HistorAI](https://apps.apple.com/app/historai), an AI-powered app for real-time video conversations with historical figures. We built our SOC 2 compliance program from scratch as a solo founder and open-sourced these templates so others don't have to start from zero.

---

## License

MIT License — see LICENSE file for details. Use freely, modify, and distribute. The only requirement is attribution.

---

## Next Steps

1. Read [SOC2-GUIDE.md](SOC2-GUIDE.md) for the full landscape
2. Read [RISK-REGISTER.md](templates/RISK-REGISTER.md) for an example of risk scoring
3. Customize all templates for your organization
4. Start with SUBPROCESSOR-TABLE.md (most urgent: know your vendors)
5. Good luck with your compliance journey!

---

**Last Updated:** April 2026
**Version:** 1.0
**Recommended For:** Solo founders, small teams, AI/voice/ML products
