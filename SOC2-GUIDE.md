# The Solo Founder's Guide to SOC 2 Compliance

*A practical guide to what SOC 2 costs, what you get, and the honest trade-offs of building your own compliance pipeline, written for AI-native products.*

**For:** AI-native products handling voice data, behavioral analytics, generative AI, and multi-vendor data pipelines

**By [Lantern Works](https://lanternworks.dev)**, makers of Valoquent, an app for real-time video conversations with historical figures. I built this SOC 2 compliance program from scratch and open-sourced the templates so others don't have to start from zero.

---

## Why This Guide Exists

An AI product carries four risks that a compliance kit has to be written around:

- **Voice and biometric data** (Twilio, ElevenLabs, Deepgram), which is new regulatory territory (GDPR, BIPA, CUBI)
- **Generative AI pipelines** (OpenAI, Anthropic), which bring prompt injection risks, training data leakage, and model-specific security questions
- **Multi-vendor architectures**, where 10 to 15 vendors process customer data and each is a potential breach point
- **Conversation data** (transcripts, user behavior), which is sensitive, long-lived, and easy to expose by accident

This guide addresses those specific challenges. It includes worked examples of AI-specific risks (prompt injection, voice data leakage, vendor pipeline management) and templates designed with voice, generative AI, and multi-vendor complexity in mind.

---

## What is SOC 2?

SOC 2 (System and Organization Controls 2) is an auditing framework developed by the AICPA that evaluates how a company handles customer data. It's the de facto trust standard for SaaS companies selling to businesses, schools, or regulated industries.

It's organized around five Trust Services Criteria categories:

1. **Security (CC1–CC9)**, protection against unauthorized access. The nine common criteria all sit inside Security, covering governance, communication, risk assessment, monitoring, control activities, logical and physical access, system operations, change management, and risk mitigation.
2. **Availability (A1)**, systems are available for operation as committed
3. **Processing Integrity (PI1)**, system processing is complete, valid, and accurate
4. **Confidentiality (C1)**, confidential information is protected
5. **Privacy (P1–P8)**, personal information is handled in accordance with commitments

The version in force is TSP Section 100, the 2017 criteria, with revised points of focus issued in 2022. Points of focus are explanatory examples that sit beneath the criteria, so the 2022 revision changed no control requirements. System descriptions are written against the AICPA's 2018 description criteria (DC 200), whose implementation guidance was revised in 2022; that revision left every description criterion unchanged.

There are two report types:

- **Type I**, a snapshot: "Do you have the right controls designed?" (point-in-time)
- **Type II**, sustained: "Have your controls been operating effectively for 3 to 12 months?" (period-of-time)

A common path is Type I first, then Type II. Security is the only required category, and the other four are optional add-ons based on customer requirements.

---

## Who Actually Needs SOC 2?

**You likely need it if:**

- You're selling to enterprises, schools, healthcare, or government organizations
- A potential customer or partner has asked "Are you SOC 2 compliant?"
- You handle user data that flows through multiple third-party AI services
- You want to differentiate from competitors on trust
- You're building in a regulated or regulation-adjacent space (education, health, finance)

**Even if you're pre-launch, start now.** A solo founder implementing controls on a fresh codebase might spend 40 hours. The same controls retrofitted onto a 3-year-old codebase with 5 developers could take 400+ hours. Your architecture decisions, vendor choices, and data flow patterns are dramatically easier to get right before you have users than after, which makes building with compliance in mind from day one the cheaper architecture.

---

## What It Costs in 2026

I sourced these figures in September 2026 from published prices, CPA firms' own guidance, and the compliance vendors' pricing guides. No CPA firm I checked publishes a rate card, so the audit fees for very small teams rest on directories and vendor guides, and they move. Get quotes before you budget. Hour and week estimates marked *my estimate* come from my own build and have no outside source.

### Option 1: Full-Service (Consulting Firm + Auditor)

| Item | Cost | Timeline |
|------|------|----------|
| Compliance consultant (gap assessment, policy writing, control design) | $3,000–$25,000, or $1,800–$9,000/month on retainer | 2–4 months |
| SOC 2 Type I audit (CPA firm) | $15,000–$40,000 | 1–2 months |
| SOC 2 Type II audit (CPA firm) | $20,000–$60,000 | 3–12 month observation + 1–2 month report |
| Annual re-audit (the next Type II) | $15,000–$50,000/year | Ongoing |
| **Total Year 1** | **$38,000–$125,000** | **6–18 months** |

The traditional path. In my judgment it fits funded startups with $1M+ ARR or firm enterprise sales requirements. Consultant figures come from published small-company offers ([SOC2Auditors.org readiness directory](https://soc2auditors.org/soc-2-readiness-firms/), [Iron Fort on AWS Marketplace](https://aws.amazon.com/marketplace/pp/prodview-xow2pz4ykypja)); audit bands from the [SOC2Auditors.org cost survey](https://soc2auditors.org/soc-2-audit-cost/) and [Vanta](https://www.vanta.com/collection/soc-2/soc-2-audit-cost).

### Option 2: Compliance Platform (Vanta, Drata, Secureframe, Thoropass, Sprinto)

| Item | Cost | Timeline |
|------|------|----------|
| Platform subscription | $10,000–$25,000/year | Ongoing |
| Audit (often bundled or discounted through the platform) | $5,000–$20,000 | 1–2 months |
| Internal time (you still do the work) | 80–200 hours (*my estimate*) | 2–4 months |
| **Total Year 1** | **$15,000–$45,000** | **3–6 months** |

The smallest tiers list at $8,700 to $32,500 a year on AWS Marketplace ([Vanta](https://aws.amazon.com/marketplace/pp/prodview-5ophamrbfxt44), [Drata](https://aws.amazon.com/marketplace/pp/prodview-3ubrmmqkovucy), [Thoropass](https://aws.amazon.com/marketplace/pp/prodview-3fqzxq4nazmgu)), and [Vendr's purchase medians](https://www.vendr.com/marketplace/vanta) for the main platforms run $15,000 to $25,000. Platforms automate evidence collection, provide policy templates, and connect you with auditors. Policies, vendor management, access reviews and training are still your work.

**Best for (my judgment):** startups with $500K+ ARR, a small team, and active enterprise sales.

### Option 3: DIY (This Starter Kit + GitHub Actions + Your Time)

| Item | Cost | Timeline |
|------|------|----------|
| Policy documents and control mapping | $0 (this kit) | 1–2 weeks (*my estimate*) |
| CI security pipeline you build in your own repo | $0 (GitHub Actions: 2,000 min/month free for private repos; public repos are free) | 1 day setup (*my estimate*) |
| Compliance tracker | $0 (a spreadsheet, or a self-hosted open-source platform such as [Comp AI](https://github.com/trycompai/comp) or [Probo](https://github.com/getprobo/probo)) | Ongoing maintenance |
| Your time | 40–80 hours total (*my estimate*) | 2–4 weeks |
| SOC 2 Type I audit (when ready) | $5,000–$15,000 for 1–10 people, Security only | 1–2 months |
| **Total pre-audit** | **$0** | **2–4 weeks** |
| **Total including audit** | **$5,000–$15,000** | **2–5 months** |

This is what this starter kit enables. You do the control design and evidence collection yourself, then engage an auditor when you're ready. The audit is the one cost you can't DIY, because a CPA firm has to issue the report. Small-team audit figures: [SOC2Auditors.org](https://soc2auditors.org/soc-2-audit-cost/), [Secureleap](https://www.secureleap.tech/blog/soc-2-certification-cost), [Drata](https://drata.com/learn/soc-2/cost); Actions minutes: [GitHub Docs](https://docs.github.com/en/billing/concepts/product-billing/github-actions).

**Best for:** Solo founders, bootstrapped startups, pre-revenue or early-revenue companies building the right habits now.

### A Penetration Test, If a Buyer Asks

SOC 2 does not require one; penetration testing is one of several evaluations the CC4.1 points of focus list. Enterprise buyers ask for one anyway. Published starting prices for a manual test of one web application run from $3,000 to $10,800 ([Penti](https://penti.ai/pricing), [Astra](https://www.getastra.com/pricing), [Software Secured](https://www.softwaresecured.com/pricing)), and a mobile app from $5,400.

---

## Benefits of SOC 2 Compliance

### Business Benefits

- **Unlocks enterprise sales.** Many enterprise procurement teams won't evaluate you without SOC 2, so treat it as the price of entry.
- **Shortens sales cycles.** Instead of answering a 200-question security questionnaire for every prospect, you hand them your SOC 2 report.
- **Signals maturity.** For a solo founder, "SOC 2 controls implemented" tells investors and partners you're building a real business.
- **Competitive advantage.** A documented compliance posture is something you can hand a prospect on the day they ask, and it answers a question your competitors will still be drafting a response to.
- **Required for regulated verticals.** Education (FERPA adjacency), healthcare (HIPAA foundation), finance (SOX adjacency). SOC 2 is the entry ticket in all three.

### Technical Benefits

- **You find real bugs.** The process of documenting your data flows, vendor relationships, and access controls surfaces issues you didn't know you had. I found committed private keys and missing deletion logic in my own codebase.
- **Better architecture decisions.** When you know you'll need to explain your data flow to an auditor, you make cleaner architecture choices.
- **Automated security scanning.** A CI pipeline in your own repo catches vulnerabilities on every push, which turns vulnerability management into a continuous control.
- **Incident readiness.** Having a documented incident response plan means you're not improvising at 2am when something goes wrong.

### Personal Benefits (Solo Founder)

- **Sleep better.** Knowing you've thought through security systematically reduces the ambient anxiety of running a production app.
- **Credibility in conversations.** When a potential partner asks about security, you have real answers instead of hand-waving.
- **Reusable across projects.** Once you've built the compliance muscle, it applies to every future product.

---

## The Honest Downsides of Building Your Own Pipeline

This kit saves you the $3,000–$25,000 a small company pays a consultant. It also comes with real trade-offs:

### 1. You're the Expert and the Executor

With Vanta/Drata, you get guided workflows that tell you "do this next." With DIY, you need to understand the framework well enough to prioritize your own work. This kit helps, but you're still making judgment calls about what matters most for your specific situation.

### 2. No Continuous Infrastructure Monitoring

Compliance platforms integrate with AWS/GCP/Azure to continuously monitor your cloud configuration: are your S3 buckets public? Are your security groups too permissive? Is MFA enabled on all IAM accounts? If you're on raw cloud infrastructure, you'll need to build this monitoring yourself or accept the gap.

**Mitigating factor:** If you're on a managed platform (Replit, Vercel, Railway, Render), your hosting provider handles infrastructure security. Their SOC 2 report covers the infrastructure layer. This is actually a significant advantage of managed platforms for solo founders.

### 3. No Employee Endpoint Monitoring

Vanta can verify that every laptop in your company has disk encryption, a password manager, and MDM installed. As a solo founder you're the only "employee," so this matters less. When you hire, you'll need to solve it.

### 4. No Auditor Portal

Compliance platforms provide a branded portal where your auditor logs in, reviews evidence, and checks off controls. With DIY, you'll share a Google Drive folder, a GitHub repo, or a Notion workspace. It works, but it's less polished.

### 5. Manual Evidence Collection

CI you set up in your own repo automates code-level evidence (security scans, dependency audits, change logs). Organizational evidence (vendor DPA status, access reviews, policy acknowledgments, training records) is still manual. You're maintaining spreadsheets by hand.

### 6. No Built-In HR Integration

When you hire employee #2, you'll need to document onboarding/offboarding security procedures, background checks, and security training. Compliance platforms integrate with HR tools (Gusto, Rippling) to automate this. With DIY, it's a checklist in a doc.

### 7. You Might Miss Something

Professional compliance consultants have done this hundreds of times. They know what auditors look for and what gaps are common. As a solo founder, you might over-invest in one area and under-invest in another. This kit is comprehensive, but it's not a substitute for an experienced auditor's eye.

### When to Graduate

My rule of thumb: use DIY until the maintenance burden exceeds 4–5 hours/month, or until you hire employee #4–5 and need endpoint monitoring and HR integrations. At that point a platform at $15,000–$25,000 a year starts earning its keep.

---

## SOC 2 for AI Apps: Special Considerations

Traditional SOC 2 guidance was written for conventional SaaS apps. AI applications have additional considerations:

### Multi-Vendor Data Pipelines

Every AI service you add (an LLM provider, a voice API, an avatar generator, an embedding service) is another third party receiving user data. Each vendor is a subprocessor that needs a security assessment, a DPA, and clear documentation of what data they receive and retain. The `SUBPROCESSOR-TABLE.md` template is designed for this.

### AI Model Training Opt-Outs

Users and auditors will ask: "Is my data used to train AI models?" You need a documented answer for every vendor, because the defaults differ. As of 2026-09-30, the [OpenAI API](https://developers.openai.com/api/docs/guides/your-data), the [Claude API](https://www.anthropic.com/legal/commercial-terms) and the paid tier of the [Gemini API](https://ai.google.dev/gemini-api/terms) do not train on your data, while [Deepgram](https://developers.deepgram.com/trust-security/your-data) and [ElevenLabs](https://elevenlabs.io/terms-of-use) use it to improve their models unless you opt out (per request at Deepgram, an account setting at ElevenLabs). Retention is a separate setting: a vendor that never trains on your data can still keep it for weeks for abuse monitoring. Record both answers for each vendor in `VENDOR-ASSESSMENT.md` (sections 9.1 and 9.4), and keep a screenshot or config export of each opt-out as evidence.

### Voice and Biometric Data

Voice audio becomes biometric data in most laws only when it is turned into, or can yield, something that identifies the speaker. Under the GDPR, voice is special-category data when processed to uniquely identify someone. Illinois BIPA and Texas CUBI cover voiceprints and list no recordings, and courts applying BIPA ask whether the data can identify a person; since 2026-01-01 Texas also exempts voiceprints used to develop or offer AI systems unless the system is used to identify people. Connecticut excludes audio recordings unless data from them is generated to identify someone, and Washington's biometric law excludes recordings and the data generated from them. Colorado excludes recordings from "biometric data" unless used to identify, but treats a voiceprint, or other data that can be processed to uniquely identify someone, as a "biometric identifier", with notice and deletion duties at any volume since 2025-07-01. California and Washington's My Health My Data Act count a recording from which a voiceprint can be extracted. So the deciding question is whether you or a vendor create a voiceprint or speaker model from the audio. Children's audio is the exception: under COPPA, audio kept only to answer a child's request must be deleted immediately.

### Prompt Injection and AI-Specific Security

The Trust Services Criteria contain no AI-specific control, and auditors work the topic through the general criteria instead: they ask about prompt injection prevention, AI output validation, hallucination handling in user-facing content, and data isolation between users, then map your answers onto CC6 and CC7.

Two things outside SOC 2 cover that ground and reach your product directly: a set of laws requiring you to tell people they are talking to AI, and ISO/IEC 42001, the management-system standard buyers ask for when a SOC 2 report does not answer their AI questions. Both are covered below.

### The "Is This Healthcare?" Question

If your AI app could plausibly be used for therapeutic, clinical, or wellness purposes, you may be adjacent to HIPAA territory. SOC 2 is a foundation for HIPAA readiness but doesn't replace it. HIPAA adds Business Associate Agreements, specific breach notification timelines (no later than 60 calendar days after discovery), and stricter data handling requirements. An app outside HIPAA that keeps a personal health record drawing on several sources can fall under the FTC Health Breach Notification Rule, with the same 60-day limit. Check whether each AI and voice vendor offers a BAA before you build on it; a vendor without one can be an architectural blocker.

---

## Telling People They Are Talking to AI

Several jurisdictions now require you to disclose that a person is interacting with an AI system, and to mark content your system generates. These duties sit outside SOC 2 entirely, they apply whether or not you ever pursue an audit, and the trigger is usually where your *users* are. A solo founder in one country with users in another is inside the second country's rules.

The obligations differ enough that treating any one of them as the global template will leave gaps. The table is correct as of 2026-09-30.

| Where | What it requires | Since | Reaches a small team? |
|---|---|---|---|
| **European Union** (AI Act Art 50) | Tell people they are talking to AI unless it is obvious; the Commission expects reminders for companions and children and a spoken notice at the start of voice. Mark generated audio, image, video and text machine-readably. Deployers label deepfakes. ([FAQ](https://digital-strategy.ec.europa.eu/en/faqs/transparency-obligations-under-article-50-ai-act); [guidelines](https://digital-strategy.ec.europa.eu/en/library/guidelines-transparency-obligations-providers-and-deployers-ai-systems)) | 2026-08-02. Systems on the market before then have until 2026-12-02 for marking only. | Yes, if people in the EU can use it. No revenue floor. |
| **China** (Labelling Measures; Order No. 21) | Visible labels on generated content of the deep-synthesis kinds and metadata labels in generated files. Companion-style services also tell users they are talking to AI and remind them after two hours of continuous use. ([Measures](https://www.cac.gov.cn/2025-03/14/c_1743654684782215.htm); [Order No. 21](https://www.cac.gov.cn/2026-04/10/c_1777558395078289.htm)) | 2025-09-01; Order No. 21 from 2026-07-15 | Only if you serve the public in mainland China. |
| **South Korea** (AI Basic Act Art 31) | Tell users in advance the product runs on generative AI. Mark outputs as AI-generated; output hard to tell from real needs a mark people can see or hear. ([korea.kr](https://www.korea.kr/news/policyNewsView.do?newsId=148954629); [FPF](https://fpf.org/blog/south-koreas-new-ai-framework-act-a-balancing-act-between-innovation-and-regulation/)) | 2026-01-22. Fines deferred to about 2027-01-22 at the earliest. | Yes; it reaches providers abroad. A local representative is needed only at large scale (1,000,000 daily Korean users or big revenue). |
| **Vietnam** (AI Law Art 11) | Tell users they are interacting with AI. Mark generated audio, image and video machine-readably. Label content imitating real people or events. ([official translation](https://en.baochinhphu.vn/viet-nams-law-on-artificial-intelligence-111260715113551787.htm)) | 2026-03-01. Earlier systems: 2027-03-01, or 2027-09-01 in health, education, finance. | Yes; it covers foreign organisations active in Vietnam. |
| **India** (IT Rules 3(3)) | Services that let users make realistic synthetic audio, images or video label it visibly or with an audio prefix, embed permanent metadata, and block unlawful deepfakes. Text is outside. ([MeitY](https://www.meity.gov.in/static/uploads/2026/02/550681ab908f8afb135b0ad42816a1c9.pdf)) | 2026-02-20 | Binds "intermediaries"; whether an AI app is one is unsettled. |
| **Peru** (Law 31814 regulation) | Tell users beforehand what the AI system does; visibly identify AI-generated content. ([El Peruano](https://elperuano.pe/noticia/304002-ley-de-ia-desde-el-jueves-10-de-setiembre-se-activan-obligaciones-especificas-para-cinco-sectores)) | 2026-09-10 in health, education, justice, security, finance; other sectors by 2029-09-10 | Yes in those sectors; small firms get later dates. |
| **United Kingdom** | No AI disclosure law. UK GDPR transparency (Arts 5(1)(a), 13, 14) means the interface should make the machine apparent. OSA s.216A only lets ministers extend illegal-content duties to AI services. ([s.216A](https://www.legislation.gov.uk/ukpga/2023/50/section/216A)) | In force | Through data protection law only. |
| **Japan** (AI Promotion Act) | No disclosure or marking duty; businesses are asked to cooperate with government measures. No penalties. ([outline](https://www.japaneselawtranslation.go.jp/outline/168/905R744.pdf)) | 2025-06-04 | No. |
| **Canada** | No binding AI statute. AIDA died in January 2025; Bill C-34 (online harms, including some AI chatbots) is at second reading. ([LEGISinfo](https://www.parl.ca/legisinfo/en/bill/45-1/c-34)) | n/a | No disclosure duty. |
| **United States** (federal) | No disclosure or marking statute. No federal action has preempted a state law. ([Federal Register](https://www.federalregister.gov/api/v1/documents.json?conditions%5Bterm%5D=Executive%20Order%2014365&conditions%5Bpublication_date%5D%5Bgte%5D=2026-09-01)) | n/a | No. |
| **California** (SB 243; SB 942 as amended by SB 1000) | Companion chatbots: say the bot is AI where a person could be misled, and publish a self-harm protocol. Anyone producing a generative AI system open to Californians: embed a hidden provenance disclosure in generated image, video and audio, and offer a free checking tool. ([SB 1000](https://leginfo.legislature.ca.gov/faces/billTextClient.xhtml?bill_id=202520260SB1000)) | SB 243 2026-01-01; SB 942 2026-08-02, user floor removed 2026-09-30 | Yes, both. SB 243 excludes customer-service and productivity tools and carries a private right of action at $1,000 per violation. SB 942 excludes text and non-user-generated games. |
| **New York** (GBL Art 47) | AI companions: tell users they are not talking to a human at the start (once a day is enough) and every three hours. ([1702](https://www.nysenate.gov/legislation/laws/GBS/1702)) | 2025-11-05 | Yes; no floor. |
| **Colorado** (HB 26-1263) | Any public conversational AI: disclose AI at the first interaction each day, every three hours or persistently, and when asked. ([HB 26-1263](https://leg.colorado.gov/bills/hb26-1263)) | 2027-01-01 | Yes; no companion test, no floor. |
| **Hawaii** (Act 248) | AI companions: a clear notice that they are AI wherever a person would think them human. ([CD1](https://data.capitol.hawaii.gov/sessions/session2026/bills/SB3001_CD1_.HTM)) | 2026-07-14 | Yes, for products with accounts or profiles. |
| **Maine** (10 MRSA 1500-DD) | A clear notice when a chatbot used in trade could make a consumer think they are talking to a person. ([1500-DD](https://legislature.maine.gov/statutes/10/title10sec1500-DD.html)) | About 2025-09-24 | Yes. |
| **Utah** (Code 13-77) | Say it is AI when a consumer clearly asks; licensed professionals disclose up front in high-risk uses. Clear disclosure throughout earns a safe harbor. ([13-77](https://le.utah.gov/xcode/Title13/Chapter77/C13-77_2025050820250508.pdf)) | 2025-05-07 in this form | Yes; $2,500 per violation. |
| **Texas** (TRAIGA) | The disclosure duty binds government agencies and health care providers; private products face intent-based bans only. ([HB 149](https://capitol.texas.gov/tlodocs/89R/billtext/pdf/HB00149F.pdf)) | 2026-01-01 | In scope, though not for disclosure. |

Taiwan's AI Basic Act binds government only, and Singapore's chatbot guidelines are voluntary, so neither gets a row. For cadence and build detail duty by duty, the sibling [Chatbot Compliance Kit](https://github.com/ann-ette/chatbot-compliance-kit) has a card for each: the notice cadence, answering "are you human," a persistent label, machine-readable marking, and disclosure at onboarding and purchase.

### What to Actually Build

The engineering work is smaller than the table suggests, because one honest implementation satisfies most of it:

- **Disclose in the interface, at the point of interaction.** A line in your privacy policy does not meet the UK reading and does not meet the EU "obvious to a reasonably informed person" test. Put it where the conversation starts.
- **Name the system, and repeat the notice where it is expected.** An interface that says which assistant a user is talking to covers the basic EU duty. The Commission's guidelines go further for two cases: a spoken statement at the start of a voice conversation, and periodic reminders in companion-style products and anything children use. New York, Colorado and China set their own reminder intervals.
- **Mark generated output machine-readably.** Metadata or a watermark on generated text, images and audio. In the EU, products already on the market before 2026-08-02 have until 2026-12-02. California's duty for generated image, video and audio applies now, with a free tool people can use to check a file. This is the item most likely to need real code.
- **Write the self-harm protocol down and publish it** if anything you ship could be read as a companion. California attached a private right of action to this one, so it carries direct financial exposure without a regulator having to act.
- **Keep a dated record of which of these you assessed and what you concluded.** That record is the evidence an auditor wants under CC3.4 (changes that could affect internal control, which includes new law), and it is what turns a compliance question into a five-minute answer next year.

**A scoping note.** I am not a lawyer and this is not legal advice. What the table gives you is the shape of the duty and where to look; a product doing anything unusual should get the specific question answered properly.

---

## What ISO 42001 Covers That SOC 2 Does Not

When an enterprise buyer sends a questionnaire with AI governance questions on it, a SOC 2 report cannot answer several of them, and this is the standard they are usually reaching for. ISO/IEC 42001 specifies an AI management system, in the same way ISO 27001 specifies an information security management system.

Where the frameworks land:

| The buyer's question | SOC 2 | ISO 27001 | ISO 42001 |
|---|---|---|---|
| Are your operational controls independently attested? | Yes | Partly | Partly |
| Is your information security formally managed? | Partly | Yes | No |
| Do you have an AI policy with a named accountable executive? | No | No | Yes |
| Do you keep an inventory of every AI system in the product? | No | No | Yes |
| Is each AI system risk-classified? | No | No | Yes |
| Are AI impacts on affected people assessed? | No | No | Yes |

The three cells SOC 2 leaves blank are the whole reason 42001 exists. It requires an AI policy with executive accountability attached to a person, a formal inventory of the AI systems you operate, and a documented risk classification for each one. No Trust Services Criterion reaches any of the three.

The frameworks stack: 42001 for AI governance, 27001 for information security management, SOC 2 for independently attested operational controls. Vendors selling AI into enterprise increasingly hold all three, which is why the questions are showing up in procurement.

42001 is still its first edition, published in December 2023 with no amendment, and the European adoption, EN ISO/IEC 42001:2026, carries the same text. Two companion standards followed in 2025. ISO/IEC 42005:2025 gives guidance for the AI system impact assessment in the last row of the table above. ISO/IEC 42006:2025 sets the requirements for bodies that audit and certify against 42001, so when a vendor shows you a 42001 certificate, ask which body issued it.

### What Certification Costs, and Three Documents Worth Writing Now

42001 is an audited management system, which puts it in a different weight class from a SOC 2 Type I. Published figures for a small organization with one or two AI systems in scope cluster around $5,000 to $15,000 for the Stage 1 and Stage 2 audit, with some sources quoting up to $25,000 for a first cycle, and $15,000 to $40,000 all-in once implementation and gap remediation are counted. Surveillance audits in years two and three run roughly 30 to 40 percent of the initial fee, with full recertification every three years. Internal staff time is consistently described as the largest hidden cost.

Treat those numbers as directional. They come from consultancies and compliance vendors who sell adjacent services, and I have not verified them against a quote.

For most solo founders reading this kit, the right move is to know where the gap is. Certification is a real project, and a small team pursuing SOC 2 has better uses for the same money. What is worth doing now costs nothing: write the AI policy, list your AI systems, classify each one by risk. Those three artifacts answer most of the questionnaire, they are useful whether or not you ever certify, and they are the same documents 42001 would ask you to produce if you did.

Short of certification, there is a public option. The Cloud Security Alliance's AI Controls Matrix (v1.1, June 2026) sets out 247 control objectives and maps them to 42001, 27001 and the NIST AI RMF. Publishing its self-assessment questionnaire, the AI-CAIQ, to the CSA STAR Registry earns STAR for AI Level 1. Level 2 takes a third-party 42001 certificate plus an AI-CAIQ that has passed CSA's automated Valid-AI-ted scoring.

---

## Frequently Asked Questions

**Can I say "SOC 2 compliant" on my website before the audit?**

No. "SOC 2 compliant" or "SOC 2 certified" implies a completed audit. You can say: "SOC 2 controls implemented," "Following SOC 2 Trust Service Criteria," or "SOC 2 Type I audit planned." These are accurate and meaningful to prospects.

**Do I need all five Trust Service Criteria?**

No. Security is the only required category. Start with Security only (or Security + Confidentiality) and add others when customers ask for them.

**How long does the audit take?**

Type I: 3–6 weeks once ready. Type II: 3–12 month observation period, then 1–2 months for the report. The AICPA sets no minimum period; three months is the shortest CPA firms describe seeing in practice, and twelve is the most common. Starting your automated security pipeline early builds evidence history from day one.

**What if an auditor finds issues?**

Auditors issue "exceptions" for controls that aren't effective. A few exceptions are noted in the report and don't fail your audit. Documented remediation plans for known gaps show an auditor the program works.

**Can I use this for ISO 27001?**

There's significant overlap. ISO/IEC 27001:2022, amended in 2024 to add climate-change considerations, requires a formal ISMS with more prescribed structure, and these policies map well to its Annex A controls. If a buyer asks for a privacy certification, the ISO standard for it is ISO/IEC 27701:2025, which since October 2025 is a standalone privacy management system; certificates to the 2019 edition have to transition by 31 October 2028.

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
5. Set up a CI security pipeline in your own repository for automated evidence collection
6. Use the `COMPLIANCE-TRACKER-TEMPLATE.md` to track your progress

Total estimated time, by my own estimate: 40–80 hours spread over 2–4 weeks.

---

*Built by a solo founder, for solo founders. Open-sourced by [Lantern Works](https://lanternworks.dev).*

**Last updated:** October 2026 · **Version:** 1.3
