# SOC 2 Starter Kit for AI-Native Products

**Built for products handling voice data, behavioral analytics, generative AI, and multi-vendor data pipelines**

**Originally Published:** 2026-04-03 · **Last Updated:** 2026-10-01 · **Version:** 1.3

Maps to the 2017 Trust Services Criteria with the 2022 revised points of focus. See [What Changed in 1.3](#what-changed-in-13) for this release.

---

## What This Is

A production-ready collection of SOC 2 compliance templates for solo founders and small teams building AI-native products. The templates are written around four things an AI product actually deals with:

- **Voice and biometric data** processing (voice APIs, facial recognition, speaker ID)
- **Generative AI pipelines** (LLM APIs, fine-tuning, prompt injection risks)
- **Multi-vendor architectures** (10-15 vendors processing customer data, each a potential risk)
- **Solo founder workflow** (you fill every role; no HR, no compliance team)

The risk register is tuned to AI vendors, the subprocessor model assumes a pipeline of ten to fifteen processors, and the worked examples sit in voice and biometric territory.

**Mapped against:** TSP Section 100, the 2017 Trust Services Criteria, with the revised points of focus issued in 2022. The AICPA has published no newer criteria. System descriptions follow the 2018 description criteria (DC 200), with implementation guidance revised in 2022 that left the criteria unchanged.

**Open-sourced by [Lantern Works](https://lanternworks.dev)**, makers of Valoquent. MIT License.

---

## Who This Is For

**Perfect fit:**
- Solo founder running an AI/voice product with customers
- 2-5 person team with no dedicated compliance role
- Bootstrap or pre-Series A, with no budget for a consultant
- Building something that handles user data: conversations, voice, biometrics, behavioral data
- Want to move fast and build compliance in from the start

**Still a good fit, even if:**
- **You're pre-launch:** building with compliance in mind from day one is dramatically cheaper than retrofitting it later. Your architecture decisions, vendor choices, and data flows are easier to get right now than to fix after 10,000 users
- **You're B2C today:** enterprise, education, and healthcare partnerships come faster than you expect, and "SOC 2 controls implemented" opens doors that "we'll get to it" doesn't
- **You're building on a standard SaaS stack:** this kit still applies, though a compliance platform may be worth evaluating once you're ready for the audit itself

**What this kit can't do:** SOC 2 is an attestation report that only a licensed CPA firm can issue after examining your controls, and no template produces one. What the kit gives you is the policy, mapping and evidence work done before you hire an auditor, which is the part a small company otherwise pays a consultant $3,000 to $25,000 for ([sources in the guide](SOC2-GUIDE.md#what-it-costs-in-2026)).

---

## What's Inside

**12 templates** (5,871 lines):

1. **ARCHITECTURE-MAP.md**, eight views of how customer data moves through an AI product, from client app through real-time media, inference, and storage. Fill this in first: it feeds four of the templates below.
2. **INFORMATION-SECURITY-POLICY.md**, the foundational security policy (NIST SP 800-53 shaped)
3. **INCIDENT-RESPONSE-PLAN.md**, severity classification and response procedures
4. **RISK-REGISTER.md**, 20 risks specific to AI apps (prompt injection, voice data leakage, multi-vendor pipelines) with worked examples
5. **DATA-RETENTION-POLICY.md**, retention schedules for 27 data types with GDPR/CCPA deletion procedures
6. **CHANGE-MANAGEMENT-POLICY.md**, deployment safety (standard/significant/emergency change tiers, rollback)
7. **SUBPROCESSOR-TABLE.md**, vendor inventory, SOC 2 tracking, DPA status (critical for multi-vendor apps)
8. **VENDOR-ASSESSMENT.md**, 113 security questions for evaluating new AI vendors
9. **SECRETS-AUDIT-CHECKLIST.md**, git audit, secret rotation, automated scanning
10. **SOC2-CONTROL-MAPPING.md**, maps your controls to all 33 common criteria (CC1.1 to CC9.2) plus Availability, Confidentiality, Processing Integrity and the 18 privacy criteria, by AICPA number and in AICPA order
11. **PRIVACY-POLICY-TEMPLATE.md**, written for the GDPR, the UK GDPR, the CCPA and other US state laws, the App Store and Google Play; includes voice, biometric and AI processing sections
12. **SECURITY-PAGE-TEMPLATE.md**, public-facing trust/security page

Plus:
- **AI transparency and disclosure coverage**, in the guide and wired into the risk register (RISK-016) and the control mapping. Which jurisdictions require you to tell users they are talking to AI, what marking of generated output is owed and by when, and where a small team is in scope without a revenue floor. Seventeen rows as of 2026-09-30: the EU AI Act Article 50, China, South Korea, Vietnam, India, Peru, the UK, Japan, Canada, the US federal layer, and California, New York, Colorado, Hawaii, Maine, Utah and Texas.
- **An ISO 42001 map**, showing which AI governance questions on a buyer's questionnaire a SOC 2 report cannot answer, and what the standard costs if you decide to pursue it.
- **SOC2-GUIDE.md**, the full picture: sourced costs ($0 before the audit and about $5,000 to $15,000 with a small-team Type I, against $38,000 to $125,000 full-service), what you get, honest trade-offs
- **COMPLIANCE-TRACKER-TEMPLATE.md**, spreadsheet to track remediation and evidence

---

## Start Here: The Quick Path

**If you're a solo founder with 10 hours to invest:**

1. **Read** [SOC2-GUIDE.md](SOC2-GUIDE.md) (30 min) to understand the terrain and whether you actually need this
2. **Skim** [RISK-REGISTER.md](templates/RISK-REGISTER.md) (20 min) to see which risks apply to your app
3. **Customize & save** all 12 templates in a folder (2 hours):
   - Find/replace `[YOUR COMPANY]`, `[YOUR APP]`, etc.
   - Read the `<!-- CUSTOMIZE: -->` comments
   - Fill in placeholders for your stack (database, cloud provider, vendors)
4. **Focus your effort** (7+ hours):
   - **SUBPROCESSOR-TABLE.md**: list every vendor; get their SOC 2 reports; sign DPAs
   - **DATA-RETENTION-POLICY.md**: implement the deletion procedures (this is real code work)
   - **RISK-REGISTER.md**: document mitigations for high-risk items
   - **PRIVACY-POLICY-TEMPLATE.md**: publish on your website and App Store
5. **Gather evidence** as you implement (ongoing):
   - Save screenshots of security configs
   - Keep DPA signatures
   - Document access reviews
   - Log vendor assessments

**Timeline (my estimate): 2-4 weeks part-time, 1-2 weeks full-time.** That gets the documents in place. The fuller schedule under Implementation Timeline below runs about twelve weeks, and a Type II report then needs an observation period on top.

---

## Document Interdependencies

Some templates depend on others:

| Template | Standalone? | Depends On | Effort |
|----------|---|---|---|
| ARCHITECTURE-MAP.md | Yes | None | Half a day |
| RISK-REGISTER.md | Yes | ARCHITECTURE-MAP.md (helpful) | 1 day |
| SOC2-CONTROL-MAPPING.md | Yes | None | 2 days |
| PRIVACY-POLICY-TEMPLATE.md | Yes | None | 2 hours (customize) |
| SUBPROCESSOR-TABLE.md | Mostly | VENDOR-ASSESSMENT.md | 2-3 days (vendor outreach) |
| DATA-RETENTION-POLICY.md | Yes | None | 1 day (planning) + dev time |
| CHANGE-MANAGEMENT-POLICY.md | Yes | None | 1 day |
| VENDOR-ASSESSMENT.md | Yes | None | 1 day (template creation) |
| SECRETS-AUDIT-CHECKLIST.md | Yes | None | 1 day (tooling setup) |
| SECURITY-PAGE-TEMPLATE.md | Yes | None | 1 hour (copywriting) |

**Recommended order:**
1. Start with ARCHITECTURE-MAP (know where your data goes), then RISK-REGISTER and SOC2-CONTROL-MAPPING (understand your risks)
2. Do VENDOR-ASSESSMENT + SUBPROCESSOR-TABLE (critical: know your vendors)
3. Then PRIVACY-POLICY-TEMPLATE, DATA-RETENTION-POLICY (user-facing)
4. Then CHANGE-MANAGEMENT-POLICY, SECRETS-AUDIT-CHECKLIST (engineering practices)
5. Finally SECURITY-PAGE-TEMPLATE, SOC2-CONTROL-MAPPING refinement (trust-building)

---

## Adapting for Your Team Size

**Solo Founder:**
- You fill every role: Security Lead, Engineering Lead, Product, CEO
- Seven templates (change management, data retention, secrets audit, security page, control mapping, subprocessor table, vendor assessment) open with a "Team Size Adaptation" note explaining role placeholders
- When templates ask for sign-offs (e.g., "Security Lead and Engineering Lead approved"), you sign both lines
- This is intentional: it documents that you've reviewed and accepted responsibility for each control

**2-5 Person Team:**
- Assign roles by expertise: Who knows infrastructure best? Who handles customer security questions?
- The person closest to each domain takes responsibility, but everyone reviews
- You don't need dedicated roles; you're just documenting "who's responsible for what"

**10+ Person Team:**
- Consider graduating to a compliance platform (about $15,000 to $25,000 a year at the median, per the guide), which saves more time at scale
- Or hire a part-time compliance person (4-8 hours/week) to maintain these docs

---

## File Structure

```
soc2-starter-kit/
├── README.md                    ← Start here (this file)
├── SOC2-GUIDE.md                ← Costs, benefits, trade-offs
├── LICENSE                      ← MIT License
├── .gitignore
└── templates/
    ├── ARCHITECTURE-MAP.md                ← 8-page data-flow map, feeds four others below
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

**Recommended schedule (about twelve weeks part-time; the Quick Path above is the condensed version):**

### Week 1-2: Documentation
- [ ] Customize all templates for your organization
- [ ] Review and refine customizations
- [ ] Create internal compliance document library

### Week 3-4: Risk Assessment
- [ ] Complete RISK-REGISTER.md (20 example risks to adapt)
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
- [ ] Collect the evidence gathered so far (logs, reviews, vendor assessments)
- [ ] Verify all controls documented in SOC2-CONTROL-MAPPING.md
- [ ] Engage an external auditor if you're pursuing a report: a Type I can start now; a Type II starts an observation window (the AICPA sets no minimum, three months is the shortest CPA firms describe seeing, and twelve is the most common)

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
- A SOC 2 report (an attestation that only a CPA firm can issue after an examination)
- A substitute for ongoing security work (this is a starting point that needs upkeep)

---

## Template Statistics

Counted 2026-10-01.

- **Total Lines:** 6,741 across this README, the guide and 13 templates
- **Templates:** 12, plus the guide and the compliance tracker
- **Bracketed Placeholders:** 902 in the templates (319 of them `[DATE]`), plus 72 `CUSTOMIZE` notes
- **Control Rows:** 130, covering all 61 criteria
- **Risks:** 20
- **Example Vendors:** 15 in the subprocessor inventory, 11 with a full profile
- **Vendor Assessment Questions:** 113
- **Data Types in the Retention Table:** 27

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

**Open-sourced by [Lantern Works](https://lanternworks.dev)**, makers of Valoquent, an app for real-time video conversations with historical figures. I built this SOC 2 compliance program from scratch and open-sourced the templates so others don't have to start from zero.

---

## License

MIT License; see the LICENSE file for details. Use freely, modify, and distribute. The only requirement is attribution.

---

## Next Steps

1. Read [SOC2-GUIDE.md](SOC2-GUIDE.md) for costs, trade-offs, and the AI duties SOC 2 leaves out
2. Read [RISK-REGISTER.md](templates/RISK-REGISTER.md) for an example of risk scoring
3. Customize all templates for your organization
4. Start with SUBPROCESSOR-TABLE.md (most urgent: know your vendors)

---

### What Changed in 1.3

- Rebuilt SOC2-CONTROL-MAPPING.md on the AICPA's own criteria, because 1.2's mapping was wrong on the framework's terms: it labeled CC7 Change Management (CC7 is System Operations) and CC8 Deficiency Management (CC8 is Change Management), mislabeled CC1.1, CC1.5, CC4.2 and the privacy groups, and left out 11 of the 33 common criteria, CC9.2 vendor risk among them. The mapping now lists all 61 criteria by AICPA number and in AICPA order, with solo founder notes, a complementary controls section, and separate Type I and Type II readiness lists.
- Moved the AI disclosure rows. In 1.2 they sat under CC1.5 and P1; they now sit under CC3.4 (the dated assessment of which laws apply), CC2.3 (the notice in the interface) and P1.1 (the privacy notice).
- Expanded the guide's disclosure table to 17 jurisdictions, correct as of 2026-09-30, with California's SB 942 as amended by SB 1000, and brought RISK-016 in line with the European Commission's Article 50 guidelines.
- Sourced the guide's costs: consultant help at $3,000 to $25,000 and a small-team Type I at $5,000 to $15,000, with my own hour estimates labeled as mine.
- Named each standard by edition: ISO/IEC 42001 with its 42005 and 42006 companions, ISO/IEC 27001:2022 with its 2024 amendment, ISO/IEC 27701:2025, NIST SP 800-53 Rev 5 Release 5.2.0, and the OWASP lists, the agentic one included. Added MITRE ATLAS to the security page and the CSA AI Controls Matrix to the guide. Dropped the "July 2025 release" of the criteria that the README and guide cited; the AICPA has published no newer criteria.
- Corrected the vendor facts 1.2 had wrong, among them OpenAI, Anthropic, Google Analytics 4, Stripe and Twilio (PCI DSS sets no storage period, so Stripe's "7 years (PCI)" is gone). SUBPROCESSOR-TABLE.md gains training, retention and zero data retention columns, AI pipeline vendors for speech, voice, real-time media, avatars and embeddings, and each DPA's breach window quoted from the DPA. VENDOR-ASSESSMENT.md scores against the expected answer, rates SOC 2 Type II as High with questions for reading the report, and asks the AI questions: training defaults and opt-outs, retention and its purpose, human review, model deprecation, inference regions and ISO 42001.
- Checked the privacy material against the law as of 2026-09-30. The privacy policy template gets GDPR's one-month deadline, the full CCPA rights list and its threshold, Shine the Light under its own statute, Global Privacy Control, correct breach notice timing, Apple's own label categories and purposes, the UK's 2026 complaint and regulator changes, EU and UK transfer mechanisms, a section for other US states, and a new AI Processing section; its vendor rows are now placeholders, and Face ID and Touch ID no longer appear as data the app receives. The incident plan's notification table names California's breach statute, New York, HIPAA and the FTC Health Breach Notification Rule. The retention policy adds the biometric limits of Illinois, Texas, Colorado and Washington, privacy risk assessments and children's data, and stops citing periods no law sets. The guide now says when voice audio becomes biometric data.
- Corrected the other templates. The security page drops unearned claims and a fake SOC 2 registry URL and gets the uptime math right (99.9% allows about 43 minutes a month). RISK-017 to RISK-020 cover harmful output to vulnerable users, cost abuse, cross-user leakage and provider model changes, and RISK-002 covers indirect prompt injection. Change management covers model and prompt changes, the secrets checklist revokes a key before rewriting history, the incident plan adds AI incident types and an annual tabletop, and the security policy adds acceptable use of AI tools.
- Replaced the README's counts with measured ones (1.2 claimed 9,000+ lines and 15+ risks) and described SOC 2 as an attestation report throughout.

### What Changed in 1.2

- Added ARCHITECTURE-MAP.md, an 8-page fill-in data-flow map (system context, sessions, real-time media, inference, stores, trust boundaries, access and secrets, evidence). The repo description had advertised an architecture map that did not ship.

- Added AI transparency and disclosure coverage: a jurisdiction table in the guide (EU AI Act Art 50, China's labeling Measures, California SB 243, UK, Texas, Canada), RISK-016 in the risk register, and rows under CC1.5 and P1 in the control mapping.
- Added an ISO 42001 map: which buyer-questionnaire questions SOC 2 cannot answer, and what certification costs.
- Corrected the guide's Trust Services Criteria description. Security covers CC1 through CC9, not CC1 through CC5.
- Named the criteria vintage the kit maps to (2017 TSC with the 2022 revised points of focus).
- Corrected the template count from 9 to 12, surfacing INFORMATION-SECURITY-POLICY and INCIDENT-RESPONSE-PLAN.
- Scrubbed SOC2-CONTROL-MAPPING.md. Every control row now ships as `☐ Not Started` with a `[DATE]` placeholder, and CC1.1 is kept as a labelled worked example.
- Cleared em dashes from the templates, finishing the sweep that covered only the README and the guide in 1.1.
- Removed the GitHub Actions workflows from the README's contents. The three workflow files were never valid: two fail YAML parsing because heredoc bodies sit at column zero inside a `run:` block, and the third scans for JavaScript and Python in a repository that contains neither. They are being repaired separately and will return when they run.

**Originally Published:** 2026-04-03
**Last Updated:** 2026-10-01
**Version:** 1.3
**Recommended For:** Solo founders, small teams, AI/voice/ML products
