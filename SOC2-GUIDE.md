# The Solo Founder's Guide to SOC 2 Compliance

*A practical guide to the SOC 2 landscape, what it costs, what you get, and the honest trade-offs of building your own compliance pipeline — specifically for AI-native products.*

**For:** AI-native products handling voice data, behavioral analytics, generative AI, and multi-vendor data pipelines

**By [Lantern Works](https://lanternworks.dev)** — makers of [HistorAI](https://apps.apple.com/app/historai), an AI-powered app for real-time video conversations with historical figures. We built our SOC 2 compliance program from scratch as a solo founder and open-sourced the templates so others don't have to start from zero.

---

## Why This Guide Exists

Most SOC 2 starter kits on GitHub are built for standard SaaS: a web app on AWS, payment processing via Stripe, authentication via Auth0. These are good frameworks for that narrow use case.

But if you're building an AI product, you face different risks:

- **Voice/biometric data** (Twilio, ElevenLabs, Deepgram) — new regulatory territory (GDPR, BIPA, CUBI)
- **Generative AI pipelines** (OpenAI, Claude API, Anthropic) — prompt injection risks, training data leakage, model-specific security questions
- **Multi-vendor architectures** (10-15 vendors processing customer data, each a potential breach point) — traditional SaaS rarely touches this complexity
- **Conversation data** (conversations, transcripts, user behavior) — sensitive, long-lived, easy to accidentally expose

This guide addresses those specific challenges. It includes worked examples of AI-specific risks (prompt injection, voice data leakage, vendor pipeline management) and templates designed with voice, generative AI, and multi-vendor complexity in mind.

---

## What is SOC 2?

SOC 2 (System and Organization Controls 2) is an auditing framework developed by the AICPA that evaluates how a company handles customer data. It's the de facto trust standard for SaaS companies selling to businesses, schools, or regulated industries.

It's organized around five Trust Service Criteria:

1. **Security (CC1–CC5)** — Protection against unauthorized access
2. **Availability (A1)** — Systems are available for operation as committed
3. **Processing Integrity (PI1)** — System processing is complete, valid, and accurate
4. **Confidentiality (C1)** — Confidential information is protected
5. **Privacy (P1)** — Personal information is handled in accordance with commitments

There are two report types:

- **Type I** — Snapshot: "Do you have the right controls designed?" (point-in-time)
- **Type II** — Sustained: "Have your controls been operating effectively for 3–12 months?" (period-of-time)

Most companies start with Type I and progress to Type II. Security is the only required category — the other four are optional add-ons based on customer requirements.

---

## Who Actually Needs SOC 2?

**You likely need it if:**

- You're selling to enterprises, schools, healthcare, or government organizations
- A potential customer or partner has asked "Are you SOC 2 compliant?"
- You handle user data that flows through multiple third-party AI services
- You want to differentiate from competitors on trust
- You're building in a regulated or regulation-adjacent space (education, health, finance)

**Even if you're pre-launch, start now.** A solo founder implementing controls on a fresh codebase might spend 40 hours. The same controls retrofitted onto a 3-year-old codebase with 5 developers could take 400+ hours. Your architecture decisions, vendor choices, and data flow patterns are dramatically easier to get right before you have users than after. Building with compliance in mind from day one isn't overhead — it's cheaper architecture.

---

## The Cost Landscape in 2026

### Option 1: Full-Service (Consulting Firm + Auditor)

| Item | Cost | Timeline |
|------|------|----------|
| Compliance consultant (gap assessment, policy writing, control design) | $30,000–$80,000 | 2–4 months |
| SOC 2 Type I audit (CPA firm) | $15,000–$40,000 | 1–2 months |
| SOC 2 Type II audit (CPA firm) | $20,000–$60,000 | 3–12 month observation + 1–2 month report |
| Annual re-audit | $15,000–$50,000/year | Ongoing |
| **Total Year 1** | **$65,000–$180,000** | **6–18 months** |

The traditional path. Appropriate for funded startups with $1M+ ARR or firm enterprise sales requirements.

### Option 2: Compliance Platform (Vanta, Drata, Secureframe, Thoropass)

| Item | Cost | Timeline |
|------|------|----------|
| Platform subscription | $10,000–$25,000/year | Ongoing |
| Audit (often discounted through platform) | $10,000–$25,000 | 1–2 months |
| Internal time (you still do the work) | 80–200 hours | 2–4 months |
| **Total Year 1** | **$20,000–$50,000** | **3–6 months** |

Platforms automate evidence collection, provide policy templates, and connect you with auditors. They cover about 60–70% of what you need. The remaining 30–40% — policies, vendor management, access reviews, training — is still your work.

**Best for:** Startups with $500K+ ARR, a small team, and active enterprise sales.

### Option 3: DIY (This Starter Kit + GitHub Actions + Your Time)

| Item | Cost | Timeline |
|------|------|----------|
| Policy documents and control mapping | $0 (this kit) | 1–2 weeks |
| GitHub Actions security pipeline | $0 (GitHub free tier: 2,000 min/month) | 1 day setup |
| Compliance tracker (spreadsheet) | $0 | Ongoing maintenance |
| Your time | 40–80 hours total | 2–4 weeks |
| SOC 2 Type I audit (when ready) | $15,000–$30,000 | 1–2 months |
| **Total pre-audit** | **$0** | **2–4 weeks** |
| **Total including audit** | **$15,000–$30,000** | **2–5 months** |

This is what this starter kit enables. You do the control design and evidence collection yourself, then engage an auditor when you're ready. The audit is the one cost you can't DIY — a CPA firm has to issue the report.

**Best for:** Solo founders, bootstrapped startups, pre-revenue or early-revenue companies building the right habits now.

---

## Benefits of SOC 2 Compliance

### Business Benefits

- **Unlocks enterprise sales.** Many enterprise procurement teams won't evaluate you without SOC 2. It's table stakes, not a differentiator.
- **Shortens sales cycles.** Instead of answering a 200-question security questionnaire for every prospect, you hand them your SOC 2 report.
- **Signals maturity.** For a solo founder, "SOC 2 controls implemented" tells investors and partners you're building a real business, not a side project.
- **Competitive advantage.** Most indie AI apps have zero compliance posture. Having one sets you apart immediately.
- **Required for regulated verticals.** Education (FERPA adjacency), healthcare (HIPAA foundation), finance (SOX adjacency) — SOC 2 is the entry ticket.

### Technical Benefits

- **You find real bugs.** The process of documenting your data flows, vendor relationships, and access controls surfaces issues you didn't know you had. We found committed private keys and missing deletion logic in our own codebase.
- **Better architecture decisions.** When you know you'll need to explain your data flow to an auditor, you make cleaner architecture choices.
- **Automated security scanning.** The GitHub Actions pipeline catches vulnerabilities continuously, not just during annual reviews.
- **Incident readiness.** Having a documented incident response plan means you're not improvising at 2am when something goes wrong.

### Personal Benefits (Solo Founder)

- **Sleep better.** Knowing you've thought through security systematically reduces the ambient anxiety of running a production app.
- **Credibility in conversations.** When a potential partner asks about security, you have real answers instead of hand-waving.
- **Reusable across projects.** Once you've built the compliance muscle, it applies to every future product.

---

## The Honest Downsides of Building Your Own Pipeline

This kit saves you $20,000–$80,000 in consulting fees. But there are real trade-offs:

### 1. You're the Expert and the Executor

With Vanta/Drata, you get guided workflows that tell you "do this next." With DIY, you need to understand the framework well enough to prioritize your own work. This kit helps, but you're still making judgment calls about what matters most for your specific situation.

### 2. No Continuous Infrastructure Monitoring

Compliance platforms integrate with AWS/GCP/Azure to continuously monitor your cloud configuration — are your S3 buckets public? Are your security groups too permissive? Is MFA enabled on all IAM accounts? If you're on raw cloud infrastructure, you'll need to build this monitoring yourself or accept the gap.

**Mitigating factor:** If you're on a managed platform (Replit, Vercel, Railway, Render), your hosting provider handles infrastructure security. Their SOC 2 report covers the infrastructure layer. This is actually a significant advantage of managed platforms for solo founders.

### 3. No Employee Endpoint Monitoring

Vanta can verify that every laptop in your company has disk encryption, a password manager, and MDM installed. As a solo founder, this is less relevant — you're the only "employee." But when you hire, you'll need to solve this.

### 4. No Auditor Portal

Compliance platforms provide a branded portal where your auditor logs in, reviews evidence, and checks off controls. With DIY, you'll share a Google Drive folder, a GitHub repo, or a Notion workspace. It works, but it's less polished.

### 5. Manual Evidence Collection

The GitHub Actions pipeline automates code-level evidence (security scans, dependency audits, change logs). But organizational evidence — vendor DPA status, access reviews, policy acknowledgments, training records — is still manual. You're maintaining spreadsheets, not dashboards.

### 6. No Built-In HR Integration

When you hire employee #2, you'll need to document onboarding/offboarding security procedures, background checks, and security training. Compliance platforms integrate with HR tools (Gusto, Rippling) to automate this. With DIY, it's a checklist in a doc.

### 7. You Might Miss Something

Professional compliance consultants have done this hundreds of times. They know what auditors look for and what gaps are common. As a solo founder, you might over-invest in one area and under-invest in another. This kit is comprehensive, but it's not a substitute for an experienced auditor's eye.

### When to Graduate

The honest answer is: use DIY until the maintenance burden exceeds 4–5 hours/month, or until you hire employee #4–5 and need endpoint monitoring and HR integrations. At that point, Vanta/Drata's $15–25K/year subscription starts earning its keep.

---

## SOC 2 for AI Apps: Special Considerations

Traditional SOC 2 guidance was written for conventional SaaS apps. AI applications have additional considerations:

### Multi-Vendor Data Pipelines

Most AI apps send user data through 5–15 third-party services (LLM providers, voice APIs, avatar generators, embedding services). Each vendor is a subprocessor that needs a security assessment, a DPA, and clear documentation of what data they receive and retain. The `SUBPROCESSOR-TABLE.md` template is designed for this.

### AI Model Training Opt-Outs

Users and auditors will ask: "Is my data used to train AI models?" You need documented answers for every vendor. Most enterprise API plans include contractual commitments, but verify and document this per provider.

### Voice and Biometric Data

If your app processes voice audio, some jurisdictions classify this as biometric data (Illinois BIPA, EU GDPR, Texas CUBI). Your data handling procedures need to account for this even if you don't store audio long-term.

### Prompt Injection and AI-Specific Security

SOC 2 doesn't have specific AI controls yet, but auditors increasingly ask about prompt injection prevention, AI output validation, hallucination handling in user-facing content, and data isolation between users.

### The "Is This Healthcare?" Question

If your AI app could plausibly be used for therapeutic, clinical, or wellness purposes, you may be adjacent to HIPAA territory. SOC 2 is a foundation for HIPAA readiness but doesn't replace it. HIPAA adds Business Associate Agreements, specific breach notification timelines (60 days), and stricter data handling requirements. Many AI/voice vendors don't offer BAAs — this can be an architectural blocker.

---

## Frequently Asked Questions

**Can I say "SOC 2 compliant" on my website before the audit?**

No. "SOC 2 compliant" or "SOC 2 certified" implies a completed audit. You can say: "SOC 2 controls implemented," "Following SOC 2 Trust Service Criteria," or "SOC 2 Type I audit planned." These are accurate and meaningful to prospects.

**Do I need all five Trust Service Criteria?**

No. Security is the only required category. Most startups start with Security only (or Security + Confidentiality) and add others based on customer requirements.

**How long does the audit take?**

Type I: 2–6 weeks once ready. Type II: 3–12 month observation period + 2–6 weeks for the report. Starting your automated security pipeline early builds evidence history from day one.

**What if an auditor finds issues?**

Auditors issue "exceptions" for controls that aren't effective. A few exceptions don't fail your audit — they're noted in the report. Having documented remediation plans for known gaps actually demonstrates maturity.

**Can I use this for ISO 27001?**

There's significant overlap. ISO 27001 requires a formal ISMS with more prescribed structure, but these policies map well to ISO 27001 Annex A controls.

**Is this legally reviewed?**

No. These are templates based on industry best practices. Have legal counsel review any policy before publishing, particularly the privacy policy and compliance claims.

**What about GDPR / CCPA?**

SOC 2 and privacy regulations are complementary but different. SOC 2 focuses on your controls and processes. GDPR/CCPA focus on user rights and consent. The privacy policy template in this kit addresses both, but they're separate compliance obligations.

---

## Getting Started

1. Read through the [README](README.md) for the template index and setup instructions
2. Start with `SOC2-CONTROL-MAPPING.md` to understand what controls you need
3. Customize the `INFORMATION-SECURITY-POLICY.md` as your foundational document
4. Work through the remaining templates in order
5. Set up the GitHub Actions pipeline for automated evidence collection
6. Use the `COMPLIANCE-TRACKER-TEMPLATE.md` to track your progress

Total estimated time: 40–80 hours spread over 2–4 weeks.

---

*Built by a solo founder, for solo founders. Open-sourced by [Lantern Works](https://lanternworks.dev).*
