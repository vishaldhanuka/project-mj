# Immigration Lawyer — Flow, Messaging & Data Spec

> **Template:** B (Expert-First)
> **File:** `builds/legal/immigration-lawyer/index.html`
> **Last updated:** 2026-03-08

---

## Table of Contents
1. [User Flow Diagram](#1-user-flow-diagram)
2. [Screen-by-Screen Spec](#2-screen-by-screen-spec)
3. [Data Layer — Full Content Reference](#3-data-layer)
4. [Expert Matching Logic](#4-expert-matching-logic)
5. [Design Decisions & Rationale](#5-design-decisions--rationale)
6. [Open Questions & Known Tradeoffs](#6-open-questions--known-tradeoffs)

---

## 1. User Flow Diagram

```
Landing Page (+ sticky mobile CTA bar)
  │
  ├─ Hero CTA: "Get Matched — Describe Your Case"
  │
  ├─ Situation Picker (quickstart — skips intake-1)
  │
  └─ Bottom CTA: "Get Matched with an Attorney"
        │
        ▼
┌─ Intake Step 1: Visa Type ──────────────┐
│  Select from 7 visa categories           │
│  CTA: "Continue"                         │
│  Back → Landing                          │
└──────────────────────────────────────────┘
        │
        ▼
┌─ Intake Step 2: Situation ──────────────┐
│  5 situation options per visa type       │
│  + optional free-text description        │
│  CTA: "Find My Attorney"                │
│  Back → Intake 1                         │
└──────────────────────────────────────────┘
        │
        ▼
┌─ Match Screen (Assessment + Urgency) ───┐
│  1. Case Assessment paragraph            │
│  2. "What happens next" callout          │
│  3. Single matched expert card           │
│  4. Urgency picker (inline, optional)    │
│  5. Case summary (review of inputs)      │
│  CTA: "Talk to [Name] Now"              │
│  Back → Intake 2                         │
└──────────────────────────────────────────┘
        │
        ▼
┌─ Payment Screen ────────────────────────┐
│  1. Expert continuity strip (navy)       │
│  2. Value proposition (what you get)     │
│  3. Price: $65 today + anchoring         │
│  4. CC form (email, card, exp, cvv, zip) │
│  5. Legal disclaimer                     │
│  6. Trustpilot bar + trust badges        │
│  CTA: "Start Consultation"              │
│  Back → Match                            │
└──────────────────────────────────────────┘
        │
        ▼
┌─ Confirmation ──────────────────────────┐
│  "You're Connected!"                     │
│  Expert card: "Reviewing your case now"  │
│  CTA: "Start a New Consultation"         │
└──────────────────────────────────────────┘
```

**Shortcut:** Clicking a situation card on the landing page sets visa type + skips to Intake 2.

---

## 2. Screen-by-Screen Spec

### Screen 1: Landing Page

| Section | Content | Purpose |
|---------|---------|---------|
| **Header** | Logo (Ask a Lawyer On Call) + "Contact Us" link | Brand, sticky nav |
| **Hero Badge** | "🟢 Immigration Attorneys Online Now" | Implies live availability (removed specific count) |
| **Hero Headline** | "Talk to a verified *Immigration Attorney* — right now" | Clear value prop, urgency |
| **Hero Subtext** | "H-1B, green card, DACA, asylum, family petition. No appointment. No retainer. A licensed attorney who handles your exact case type." | Scope + differentiation |
| **Hero Trustpilot** | "★★★★★ 4.8/5 on Trustpilot · 11,000+ verified reviews" | Trust at entry point |
| **Hero Expert Cards** | 3 real expert cards (Guillermo S., Judith L., Denise C.) with JustAnswer CDN photo, specialties, verified stats, online status | Social proof, real attorneys |
| **Hero CTA** | "Get Matched — Describe Your Case" | Primary action |
| **Hero Note** | "**4 min** avg. attorney response · 100% satisfaction guarantee" | Risk reduction |
| **Hero Tags** | H-1B Visa, Green Card, DACA, Family Petition, Asylum, RFE Response, Deportation | SEO + relevance signaling |
| **Proof Bar** | 9,000+ Immigration cases · 4.8 ★ Avg. rating · 4 min Avg. response · 98% Satisfied | Authority |
| **Situation Picker** | "What's your immigration situation?" — 6-card grid (H-1B, Green Card, Family, DACA, Asylum, Other) | Soft CTA, quickstart into intake |
| **How It Works** | 3 steps: Tell us → Get matched → Chat until satisfied | Process clarity |
| **Testimonials header** | "Rated 4.8/5 on Trustpilot · 11,000+ reviews" | Authority anchor |
| **Testimonials** | 4 real Trustpilot reviews: Bryan R. 5★ (immigration knowledge), Mysti D. 5★ (life changing advice), Treasure 4★ (exceeded expectations), Verified Customer 5★ (road map in 30 min). Sources: trustpilot.com/review/www.askalawyeroncall.com?search=immigration | Social proof with real reviews |
| **Bottom CTA** | "Immigration deadlines don't wait" / "A small mistake can cost you years." / "Get Matched with an Attorney" | Urgency-driven secondary CTA |
| **Sticky CTA bar** | Fixed bar at bottom: "**Immigration attorneys** are online now" + "Get Matched" button. Appears when user scrolls past hero. Hidden on non-landing screens. | +8–15% landing-to-intake |
| **Footer** | BBB badge, DigiCert, Powered by JustAnswer, copyright, legal links | Trust + compliance |

### Screen 2: Pearl Chat (Simulated)

Replaces the old Intake 1, Intake 2, and Match screens with a single conversational interface. Full viewport height with its own header (site header hidden). State machine: `idle → visa-type → situation → describe → assessing → urgency → ready`.

| Phase | Pearl Says | User Input | UI Element |
|-------|-----------|------------|------------|
| **Intro** | "Hi! I’m Pearl, and I’m here to connect you with an immigration attorney who handles your exact case type." | — | Bot message |
| **Visa Type** | "What type of immigration matter do you need help with?" | Tap one of 7 quick replies | Quick reply buttons |
| **Situation** | "Got it — [visa type]. [Dynamic question from sitMap]" | Tap one of 5 quick replies | Quick reply buttons |
| **Describe** | "Thanks. Can you tell me a bit more about your specific situation?" | Free text in chat input OR tap "Skip — connect me now" | Textarea + quick reply |
| **Assessment** | "Let me analyze your case…" → typing indicator (2.5s) → personalized assessment paragraph from caseAssessments | — | Bot messages + typing indicator |
| **Roster** | — | — | Inline card: stacked avatars, "+N more" badge, 2×2 stats grid |
| **Urgency** | "One last thing — how urgent is your situation?" | Tap one of 4 quick replies | Quick reply buttons |
| **Ready** | "Perfect. I’ve got everything I need." | — | Inline CTA card: "Connect with an Attorney Now" ($65 today) |

| Element | Content | Purpose |
|---------|---------|---------||
| **Header** | Back arrow + Pearl avatar (purple gradient) + "Pearl" + "Online" status dot | Chat identity, navigation |
| **Messages area** | Scrollable chat messages, auto-scrolls to bottom | Conversational flow |
| **Input area** | Textarea (shown only during describe phase) + send button | Free-text case description |
| **Quick replies** | Pill buttons below bot messages, removed after selection | Structured choices |
| **Roster card** | Inline card with expert avatars, "+N" badge, 4-stat grid | Credibility before payment |
| **CTA card** | Navy gradient card: title, price ($65 vs $300–500/hr), CTA button, Trustpilot stars | Conversion |
| **Back** | → Landing |

#### Chat Quick Replies

**Visa Type** (7 options): Same as old Intake 1 options — H-1B, Green Card, Family, DACA, Asylum, Removal/Deportation, Other.

**Situation** (5 per visa type): Same as old Intake 2 options — dynamically rendered from `sitMap`.

**Urgency** (4 options): Immediate, This Week, This Month, No Rush.

**Describe** (1 option): "Skip — connect me now" — allows skipping free-text input.

#### Visa Types

| Key | Icon | Label | Description |
|-----|------|-------|-------------|
| `h1b` | 💼 | H-1B / Work Visa | H-1B, L-1, O-1, TN, E-2 and other work visas |
| `greencard` | 🟢 | Green Card | EB-1, EB-2, EB-3, adjustment of status, consular processing |
| `family` | 👨‍👩‍👧 | Family-Based Immigration | Spousal visa, family petition, K-1 fiancé visa |
| `daca` | 📋 | DACA / Dreamer | DACA renewal, advance parole, status questions |
| `asylum` | 🛡️ | Asylum / Refugee | Asylum application, refugee status, withholding of removal |
| `deportation` | ⚠️ | Removal / Deportation | Notice to appear, removal defense, immigration court |
| `other` | 📝 | Other / Not Sure | Naturalization, visa renewal, travel document, other questions |

### Screen 3: Payment

*Note: Old Screens 2–4 (Intake 1, Intake 2, Match) have been merged into Screen 2 (Pearl Chat).*

#### Situation Map

**H-1B / Work Visa** — Q: "What's happening with your work visa?" / Hint: "Select the closest match."

| Key | Icon | Label | Description |
|-----|------|-------|-------------|
| `denial` | ❌ | Petition denied | H-1B, L-1 or other work visa denied |
| `rfe` | 📄 | Received an RFE | Need help responding to Request for Evidence |
| `transfer` | 🔄 | Employer transfer | Changing employers, transferring sponsorship |
| `lottery` | 🎲 | H-1B lottery / cap | Registration, selection, cap-exempt questions |
| `status` | ❓ | Status question | Grace period, maintaining status, stamping |

**Green Card** — Q: "What stage of the green card process?" / Hint: "This helps match you precisely."

| Key | Icon | Label | Description |
|-----|------|-------|-------------|
| `eb` | 💼 | Employment-based filing | EB-1, EB-2 (NIW), EB-3, I-140 |
| `aos` | 📋 | Adjustment of Status | I-485, interview prep, medical exam |
| `consular` | 🏛️ | Consular processing | NVC, DS-260, embassy interview |
| `priority` | 📅 | Priority date / backlog | Visa bulletin, when will date be current? |
| `rfe` | ❌ | RFE or denial | RFE, NOID, or denial on green card case |

**Family Immigration** — Q: "What type of family immigration case?" / Hint: "Select the closest match."

| Key | Icon | Label | Description |
|-----|------|-------|-------------|
| `spouse` | 💍 | Spouse / marriage | I-130, CR-1/IR-1, marriage green card |
| `fiance` | 💑 | K-1 fiancé visa | Bringing fiancé(e) to the US |
| `parent` | 👨‍👧 | Parent or child petition | Sponsoring parent, child, or sibling |
| `interview` | 🗣️ | Interview preparation | Upcoming USCIS or embassy interview |
| `other` | 📝 | Other family matter | Adoption, derivative status, other |

**DACA / Dreamer** — Q: "What do you need help with for DACA?" / Hint: "Rules change frequently — get current guidance."

| Key | Icon | Label | Description |
|-----|------|-------|-------------|
| `renewal` | 🔄 | DACA renewal | Filing or questions about renewing |
| `parole` | ✈️ | Advance parole | Travel authorization while on DACA |
| `first` | 📝 | First-time application | Eligibility and new application |
| `path` | 🔀 | Path to green card | Options for adjusting status from DACA |
| `general` | ❓ | General questions | Policy changes, work permit, state rules |

**Asylum / Refugee** — Q: "What's your asylum or refugee situation?" / Hint: "Your information is confidential."

| Key | Icon | Label | Description |
|-----|------|-------|-------------|
| `filing` | 📄 | Filing application | I-589, one-year deadline, evidence prep |
| `interview` | 🗣️ | Interview prep | Upcoming asylum officer interview |
| `court` | 🏛️ | Immigration court | Removal proceedings, judge hearing |
| `appeal` | 📋 | Appeal or denial | BIA appeal, motion to reopen |
| `ead` | ❓ | Status / EAD questions | Work permit, travel, pending case |

**Removal / Deportation** — Q: "What is your removal / deportation situation?" / Hint: "Time is critical. We match you urgently."

| Key | Icon | Label | Description |
|-----|------|-------|-------------|
| `nta` | 📄 | Notice to Appear | Received NTA, need next steps |
| `hearing` | 🏛️ | Court hearing coming | Master calendar or individual hearing |
| `detained` | 🔒 | Detained / bond | Family member detained, bond hearing |
| `order` | ⚠️ | Removal order issued | Final order, motion to reopen, stay |
| `voluntary` | 📋 | Voluntary departure | Considering voluntary departure vs. fighting |

**Other / Not Sure** — Q: "What immigration question do you have?" / Hint: "Select the closest option or describe below."

| Key | Icon | Label | Description |
|-----|------|-------|-------------|
| `citizenship` | 🇺🇸 | Citizenship / Naturalization | N-400, interview prep, eligibility |
| `renewal` | 🔄 | Visa renewal / extension | Extending or renewing current visa |
| `travel` | ✈️ | Travel document | Re-entry permit, refugee travel document |
| `ead` | 💼 | Work authorization (EAD) | I-765, employment authorization |
| `general` | ❓ | General question | Something else not listed |

### ~~Screen 4: Intake Step 3 — Urgency~~ (Removed)

*Urgency is now asked as quick replies within the Pearl Chat screen.*

### ~~Screen 5: Match~~ (Removed)

*Case assessment, roster card, and CTA are now shown inline as chat messages/cards within the Pearl Chat screen.*

### Screen 3 (continued): Payment

| Element | Content | Purpose |
|---------|---------|---------|
| **Expert Strip** | Navy bar with 3 stacked real expert avatars, "Immigration attorneys ready to help", generic meta text | Continuity — same team from match screen roster |
| **Value Proposition** | Title: "Your [Case Type] consultation includes:" — 5 bullet items (3 case-specific from consultPlans + "Unlimited follow-up questions with your attorney" + "Responses within minutes, not days") | Crystal clear what user gets for their money |
| **Price** | "$65 today" with struck-through "$300–500/hr at a firm" anchor + "Includes 30-day membership — unlimited follow-ups. Cancel anytime." | Consultation framing with price anchoring |
| **CC Form** | Email, Card number, Exp/CVV/ZIP (3-col) | Standard payment fields |
| **Legal** | 'By clicking "Start Consultation", I agree to the Terms of Service and Privacy Policy, and to be charged $65 today. Includes a 30-day membership that renews monthly until canceled. Cancel anytime from My Account.' | Compliance |
| **CTA** | "Start Consultation" + 100% satisfaction badge | Action-oriented, not vague |
| **Trust Badges** | BBB Accredited, Google 4.9, DigiCert Secured | Trust at point of commitment |
| **Trustpilot Bar** | "★★★★★ Rated 4.8/5 on Trustpilot · 11,000+ verified reviews" | Prominent trust signal near CTA |
| **Supporting text** | "🔒 Your information is secure." | Reassurance |
| **Back** | → Chat |

### Screen 4: Confirmation

| Element | Content |
|---------|---------|
| **Icon** | Green checkmark circle |
| **Headline** | "You're Connected!" |
| **Body** | "Your matched immigration attorney is reviewing your case now. Expect a response within minutes." |
| **Expert Card** | 3 stacked real expert avatars + "Your Immigration Attorney" + "● Reviewing your case now" |
| **CTA** | "Start a New Consultation" (resets all state) |

---

## 3. Data Layer

### Experts

Real JustAnswer attorneys with verified profiles. Photos are 64×64 CDN thumbnails.

| Name | Title | Photo (CDN) | Specialties | Years | Cases | Rating | Handles |
|------|-------|-------------|-------------|-------|-------|--------|--------|
| Guillermo S. | Principal Attorney · Immigration Law · JD · Verified | gsenmartin 64×64 | H-1B & Work Visas, Green Cards, Deportation Defense | 18 | 122,700+ | 4.8 | h1b, greencard, deportation, daca, other |
| Judith L. | Immigration Attorney · J.D. · 40+ Yrs Practice · Verified | jludwic 64×64 | Asylum, Family Petition, Work Visas | 18 | 48,200+ | 4.8 | asylum, family, h1b, other |
| Denise C. | Immigration Attorney · Juris Doctor · Verified | mdlaw 64×64 | Family Immigration, DACA, Green Cards | 7 | 3,700+ | 4.9 | family, daca, greencard, asylum, deportation, other |

### Roster Stats (by visa type)

Shown on match screen roster panel. Numbers are aggregate team stats, not per-expert.

| Visa Type | Attorneys | Cases Handled | This Quarter |
|-----------|-----------|---------------|-------------|
| h1b | 23 | 1,240+ | 310+ |
| greencard | 31 | 2,100+ | 480+ |
| family | 27 | 1,870+ | 390+ |
| daca | 18 | 640+ | 150+ |
| asylum | 21 | 890+ | 210+ |
| deportation | 16 | 720+ | 170+ |
| other | 50 | 5,400+ | 1,200+ |

Additional fixed stats: Avg Rating 4.8, Avg Response 4 min.

### Case Assessments

Shown on match screen. Personalized paragraph for each visa type × situation (35 total).

#### H-1B / Work Visa

**denial:** An H-1B denial can feel overwhelming, but many denials are successfully overturned through a Motion to Reopen or appeal — especially with strong supplemental evidence. The key is identifying exactly why USCIS denied your petition and addressing those specific grounds. Acting quickly matters because filing deadlines are strict.

**rfe:** An RFE means USCIS needs more information before making a decision — it is not a denial. However, your response needs to directly address each point USCIS raised, with strong supporting documentation. Most RFE responses are due within 60–87 days, and the quality of your response often determines the outcome.

**transfer:** Transferring your H-1B to a new employer is a well-established process, but timing and compliance are critical. If your new employer files promptly, you can begin working for them as soon as the transfer petition is received by USCIS. An attorney can ensure nothing falls through the cracks during the transition.

**lottery:** The H-1B lottery process is highly competitive, with demand far exceeding the annual cap. Understanding your cap-exempt eligibility, premium processing options, and alternative visa pathways can significantly improve your chances. Many applicants have options they are not aware of.

**status:** Maintaining valid immigration status is essential — even a brief lapse can have serious consequences for future applications. Grace periods, extension timing, and re-entry rules are nuanced and depend on your specific visa type and situation. Getting clarity now can prevent costly mistakes later.

#### Green Card

**eb:** Employment-based green cards have specific eligibility criteria that vary significantly by category (EB-1, EB-2, EB-3). Choosing the right classification and building a strong petition from the start can save years of waiting. Your priority date, country of birth, and job qualifications all affect your timeline.

**aos:** Adjustment of Status (I-485) is the final major step in your green card process. Interview preparation, ensuring your documentation is complete, and understanding what to expect can make the difference between approval and delays. Most interviews last 15–30 minutes, but the questions vary by case type.

**consular:** Consular processing involves coordinating with the National Visa Center and your local embassy — each with their own procedures and timelines. Proper preparation of your DS-260, civil documents, and financial evidence is critical. Embassy interviews can be stressful, but thorough preparation leads to smooth outcomes.

**priority:** Priority date backlogs vary dramatically by preference category and country of birth. Understanding where your date falls in the Visa Bulletin and what options exist to potentially expedite your case (NIW, EB-1 upgrade, cross-chargeability) can be the difference between years of waiting and a faster path.

**rfe:** An RFE or denial on a green card case needs immediate, careful attention. The response must directly address USCIS concerns with strong evidence, and the filing deadline is strict. If your case was denied, you may have options including a Motion to Reopen, appeal, or refiling with a stronger case.

#### Family Immigration

**spouse:** Marriage-based immigration is one of the most common pathways, but USCIS scrutinizes these petitions closely for evidence of a genuine relationship. Having proper documentation organized — joint finances, photos, communications, affidavits — is essential. Processing times vary but typically range from 12–24 months.

**fiance:** The K-1 fiancé visa process has specific requirements including meeting in person within the past two years. After your fiancé arrives in the US, you must marry within 90 days. Understanding the full timeline — from petition to adjustment of status — helps you plan and avoid gaps in status.

**parent:** Family preference petitions have different wait times depending on the relationship and your country of birth. Immediate relatives (parents of US citizens, unmarried children under 21) have no wait — but other categories can take years. Understanding your category and preparing strong documentation matters.

**interview:** USCIS and embassy interviews for family cases focus on verifying the relationship and the petitioner's ability to support the immigrant. The specific questions depend on your case type, but being well-prepared — with organized documents and consistent, honest answers — significantly improves outcomes.

**other:** Family immigration has many pathways depending on your specific situation and relationship. Whether it involves adoption, derivative status, or a unique family circumstance, an immigration attorney can assess your eligibility and identify the best path forward for your case.

#### DACA / Dreamer

**renewal:** DACA renewal requires filing before your current status expires — USCIS recommends filing 120–150 days in advance. Late renewals can create gaps in work authorization. The process is straightforward if your situation has not changed, but any arrests, travel, or address changes can complicate things.

**parole:** Advance parole for DACA recipients allows travel outside the US, but the rules have changed multiple times. Traveling without proper authorization can result in losing DACA status and triggering bars to re-entry. Understanding current policy and risks before applying is critical.

**first:** First-time DACA applications have been subject to changing policies and court orders. Eligibility depends on continuous presence, education or military service, and criminal history. An attorney can assess whether you qualify under current rules and help you build the strongest possible application.

**path:** DACA does not directly lead to a green card, but several pathways may be available depending on your situation — including marriage to a US citizen, employer sponsorship, or advance parole combined with adjustment of status. Each pathway has different requirements, risks, and timelines.

**general:** DACA policy continues to evolve through court decisions and executive action. Understanding how current changes affect your specific situation — work authorization, state-level benefits, and long-term planning — helps you make informed decisions and stay prepared for any shifts.

#### Asylum / Refugee

**filing:** The asylum filing deadline is one year from your last arrival in the US, with limited exceptions. Building a strong case requires detailed documentation of persecution, country conditions evidence, and a compelling personal declaration. The quality of your initial application significantly impacts the outcome.

**interview:** The asylum interview is your primary opportunity to present your case to the asylum officer. How you tell your story, the evidence you present, and your ability to answer follow-up questions all affect the outcome. Most interviews last 1–3 hours, and preparation is the single biggest factor in success.

**court:** Immigration court proceedings are adversarial — a government attorney will argue against your case. Having strong evidence, prepared witnesses, and a clear legal strategy is critical. Understanding the judge's expectations and the specific grounds for your claim can significantly improve your chances.

**appeal:** Appeals to the Board of Immigration Appeals (BIA) must be filed within 30 days of the immigration judge's decision. A motion to reopen requires new evidence that was not available at the time of the hearing. Both have strict procedural requirements, and the legal arguments must be precise.

**ead:** Work authorization for asylum applicants depends on your filing date and case processing timeline. Current processing times for asylum EADs vary, and there may be options to expedite. Understanding your rights while your case is pending helps you plan financially and professionally.

#### Removal / Deportation

**nta:** A Notice to Appear is a serious legal document that begins removal proceedings. You have rights in this process, including the right to an attorney and the right to present a defense. Understanding the charges against you and the available defenses is the critical first step.

**hearing:** Immigration court hearings require careful preparation whether it is a master calendar hearing or an individual merits hearing. The evidence you present, witnesses you call, and legal arguments you make can determine whether you remain in the United States. Preparation is essential.

**detained:** When a family member is detained, the priority is understanding bond eligibility and options for release. Bond hearings consider flight risk and danger to the community. Acting quickly — within days, not weeks — can make a significant difference in how long your family member remains detained.

**order:** A final removal order is serious but may not be the end of the road. Motions to Reopen, stays of removal, and emergency relief options may be available depending on your circumstances and timing. If deportation is imminent, acting immediately is critical.

**voluntary:** Voluntary departure allows you to leave the US on your own terms instead of having a removal order on your record. However, it comes with a departure deadline, bond requirements, and a 10-year bar if you fail to leave. Understanding the long-term consequences of each option is essential.

#### Other / Not Sure

**citizenship:** The naturalization process requires meeting residency, physical presence, and moral character requirements. The interview includes a civics and English test, plus questions about your application. Most eligible applicants are approved, but certain issues (travel, arrests, tax problems) can cause delays or denials.

**renewal:** Visa extensions must be filed before your current status expires. USCIS processing times vary, and late filings can result in denial and potential status violations. Understanding your eligibility, timeline, and what to do if your status expires while waiting is important.

**travel:** Travel while immigration cases are pending carries specific risks depending on your status and case type. Some travel requires advance permission, and leaving without it can result in abandonment of your application. Understanding the rules for your specific situation is critical before booking any travel.

**ead:** Employment Authorization Document processing times have been unpredictable. If your EAD expires before your renewal is processed, you may have options for automatic extensions depending on your category. Understanding these rules prevents gaps in work authorization.

**general:** Immigration law intersects with many areas — tax obligations, criminal law, employment law, and more. Even routine questions can have unexpected implications for your immigration status. Getting accurate guidance specific to your situation helps you avoid costly mistakes.

### Consultation Plans (Payment Screen)

What the user sees under "Your [Case Type] consultation includes:" — first 3 items are case-specific, plus 2 generic items appended:
- "Unlimited follow-up questions with [Expert Name]"
- "Responses within minutes, not days"

**Full consultation plan items per visa type × situation (4 items each, first 3 shown on payment):**

#### H-1B

| Situation | Item 1 | Item 2 | Item 3 | Item 4 |
|-----------|--------|--------|--------|--------|
| denial | Review your denial notice and identify grounds for appeal | Evaluate Motion to Reopen vs. new filing strategy | Assess alternative visa options (O-1, L-1, EB categories) | Timeline and next steps specific to your employer |
| rfe | Analyze the specific RFE points and what USCIS wants | Draft strategy for a strong RFE response | Review evidence you have vs. what you need | Deadline management — how much time you have and extensions |
| transfer | H-1B transfer process and your specific timeline | Employer obligations and what to watch for | Maintaining status during the transition period | Backup plan if the transfer hits roadblocks |
| lottery | Your registration status and cap-exempt eligibility | Premium processing strategy and timing | What to do if not selected — alternative pathways | Employer next steps and compliance requirements |
| status | Current visa status assessment and any risks | Grace period rules and what actions to take | Stamping and re-entry considerations | Path forward — extension, transfer, or status change |

#### Green Card

| Situation | Item 1 | Item 2 | Item 3 | Item 4 |
|-----------|--------|--------|--------|--------|
| eb | Eligibility assessment for your EB category | I-140 strategy — which classification is strongest | Priority date outlook and timeline expectations | Employer requirements and labor certification questions |
| aos | I-485 filing status and what to expect next | Interview preparation — questions they typically ask | Medical exam and supporting document checklist | Timeline from filing to approval for your category |
| consular | NVC processing status and next steps | DS-260 review and common pitfalls | Embassy interview preparation and what to bring | Processing times at your specific consulate |
| priority | Your priority date and current visa bulletin analysis | Estimated wait time based on your category and country | Options to potentially speed up the process | What to do while waiting — maintaining eligibility |
| rfe | Analyze the specific RFE or denial grounds | Response strategy and evidence needed | Deadline and filing requirements | Appeal options if the response is denied |

#### Family

| Situation | Item 1 | Item 2 | Item 3 | Item 4 |
|-----------|--------|--------|--------|--------|
| spouse | I-130 process and timeline for your situation | Evidence requirements for bona fide marriage | Interview preparation — what they look for | Work authorization and travel while pending |
| fiance | K-1 visa process and current processing times | Required documentation and evidence checklist | What happens after your fiance arrives in the US | Timeline to adjustment of status after marriage |
| parent | Petition type and eligibility for your family member | Processing timeline for your preference category | Document requirements and country-specific considerations | What your family member should prepare |
| interview | Specific questions likely for your case type | Documents to bring and how to organize them | Common mistakes to avoid at the interview | What to do if asked to provide additional evidence |
| other | Assessment of your specific family situation | Available immigration pathways for your case | Documentation and evidence requirements | Timeline expectations and next steps |

#### DACA

| Situation | Item 1 | Item 2 | Item 3 | Item 4 |
|-----------|--------|--------|--------|--------|
| renewal | Current DACA renewal process and any policy changes | Filing timeline — how early to file and what to prepare | Common issues that delay or deny renewals | Work permit continuity during the renewal period |
| parole | Advance parole eligibility and current availability | Risks and benefits of traveling on advance parole | Application process and required documents | Re-entry considerations and what to prepare |
| first | Eligibility assessment for initial DACA filing | Current policy on new applications | Required documentation and evidence | Alternative options if DACA is not available |
| path | Available pathways from DACA to permanent status | Marriage-based, employment-based, or other options | Advance parole and adjustment of status strategy | Risks and considerations for each pathway |
| general | Current DACA policy status and recent changes | Impact on your specific situation | Work authorization and state-specific rules | Long-term planning and alternative strategies |

#### Asylum

| Situation | Item 1 | Item 2 | Item 3 | Item 4 |
|-----------|--------|--------|--------|--------|
| filing | One-year filing deadline assessment | Grounds for asylum — which one fits your case | Evidence you need and how to document your claim | I-589 preparation strategy |
| interview | What the asylum officer will ask | How to present your testimony effectively | Evidence organization and presentation strategy | What happens after the interview — timeline and outcomes |
| court | Your hearing type and what to prepare | How to present your case to the immigration judge | Evidence and witness strategy | Appeal rights if the outcome is unfavorable |
| appeal | Grounds for appeal to the BIA | Motion to Reopen requirements and deadlines | New evidence that could change the outcome | Timeline and what to expect during the appeal |
| ead | Work permit eligibility and current processing times | Travel restrictions while your case is pending | How to check your case status | Timeline to final decision |

#### Deportation

| Situation | Item 1 | Item 2 | Item 3 | Item 4 |
|-----------|--------|--------|--------|--------|
| nta | What the NTA means and your rights | Available defenses for your situation | First hearing preparation and what to expect | Bond eligibility and how to stay out of detention |
| hearing | Your hearing type — master calendar vs. individual | How to present your defense | Evidence and witness preparation | Possible outcomes and what each means for you |
| detained | Bond hearing strategy and eligibility | How to communicate with detained family member | Attorney representation options | Timeline for bond and case proceedings |
| order | Options after a removal order — Motion to Reopen, stay | Deadlines and filing requirements | Voluntary departure vs. fighting the order | Emergency relief options if deportation is imminent |
| voluntary | Pros and cons of voluntary departure vs. fighting | Impact on future immigration benefits | Deadline and filing requirements | Bar to re-entry — how long and any exceptions |

#### Other

| Situation | Item 1 | Item 2 | Item 3 | Item 4 |
|-----------|--------|--------|--------|--------|
| citizenship | N-400 eligibility — residency, physical presence, moral character | Interview preparation and civics test | Common issues that cause delays or denials | Timeline from application to oath ceremony |
| renewal | Extension/renewal eligibility for your visa type | Filing timeline and required documents | What to do if your status expires before approval | Alternative options if extension is not available |
| travel | Travel document options for your immigration status | Processing times and expedite criteria | Risks of traveling while cases are pending | Re-entry preparation and what to carry |
| ead | EAD eligibility based on your current status | Processing times and expedite options | What to do if your EAD expires before renewal arrives | Work authorization bridges and gap strategies |
| general | Assessment of your specific immigration question | Available options and pathways | Documentation requirements | Recommended next steps and timeline |

---

## 4. Expert Roster Logic

**Current approach:** No single-expert matching. The Pearl chat shows an **inline roster card** with team-level stats scoped to the user's visa type, plus 3 real expert avatars as social proof.

**How it works:**
1. User selects visa type in chat → `chatRosterStats[visaType]` provides: attorney count, total cases handled, cases this quarter
2. After case assessment, an inline card renders in the chat with:
   - Headline: e.g., "23 attorneys specialize in H-1B cases"
   - All 3 expert photos as overlapping avatars + "+N more" badge
   - 2×2 stats grid: cases handled, this quarter, avg rating (4.8), avg response (4 min)
3. Card appears as part of the conversation flow, not a separate screen

**Why roster in chat instead of separate match screen:**
- Conversational delivery feels like Pearl personally assembled the information
- No screen transition needed — assessment + roster + CTA all flow naturally in chat
- Maintains the same credibility signals (team volume, real avatars) without the overhead of a separate screen

---

## 5. Design Decisions & Rationale

### Why roster panel instead of single expert match?
The original single-expert card was misleading — it promised a specific attorney ("Talk to Jessica B. Now") who might not actually be available when the user connects. The roster approach is honest: it shows team-level stats ("23 immigration attorneys have helped people with cases like yours") with 3 real expert avatars as social proof and a "+N more" badge. Credibility comes from the volume of the team, not an individual promise that might break.

### Why Pearl chat instead of multi-screen intake?
The old flow had 3 separate screens (Intake 1 → Intake 2 → Match), each requiring a button click and page transition. The CTA "Describe Your Case" promised a conversational experience but delivered rigid form selectors. The Pearl chat replaces all 3 screens with a single conversational interface where the user ACTUALLY describes their case. Benefits:
- CTA promise matches delivery ("Describe Your Case" → actual chat)
- Fewer screen transitions = less drop-off (4 screens total vs 7)
- Assessment and roster appear as natural conversation moments, not separate pages
- In production, this simulated chat is replaced by embedding the real Pearl

### Why case assessment before payment?
The user shares information (visa type, situation, details, urgency) and receives nothing back until the assessment. The case assessment is the first "give" — a personalized paragraph acknowledging their specific problem. In the chat flow, this arrives naturally after the user shares their situation, making it feel like Pearl personally analyzed their case. This earns the right to ask for payment.

### Why explicit price on payment screen?
Previous version said "Confirm to connect" without explaining what the user was paying for. Users don't enter credit card details for vague promises. The value proposition box lists exactly what they get, shows the exact price ($65/mo), and says "Cancel anytime" — no surprises.

### Why "Start Consultation" not "Confirm now"?
"Confirm now" is vague — confirm what? "Start Consultation" tells the user exactly what happens when they click. It frames the payment as the beginning of their consultation, not the end of a checkout.

### Why generic "Immigration Attorneys Online Now" badge?
The original badge said "14 Immigration Attorneys Online Now" but the system only had 3 experts — a trust time bomb. Now the badge omits a specific number and the match screen shows accurate per-visa-type counts from `rosterStats`. In production, these numbers would come from real backend data.

---

## 6. Open Questions & Known Tradeoffs

### Open Questions
- **Case assessments accuracy:** Are the 35 assessment paragraphs legally sound enough? They're written to be general knowledge, not legal advice, but should be reviewed.
- **Situation picker on landing:** Currently shows 6 cards (no deportation). Should it show all 7 visa types to match intake-1?
- **Urgency impact:** Urgency is collected but doesn't affect matching or messaging. Should "Immediate" urgency change the case assessment tone or add urgency-specific copy?
- **Free text usage:** The optional description is passed to the case summary but doesn't affect assessments or consultation plans. Is that enough?
- **Expert photo resolution:** Current photos are 64×64 CDN thumbnails. For production, larger variants may be needed (JustAnswer URL pattern suggests larger sizes exist).
- **More expert photos for rotation:** Only 3 avatars in the `experts[]` array. Could add more from the 6 other fetched profiles (Angelo M., Franco C., Queeneth E., Clay G., Anita J., LegalClarity) for variety or rotation.
- **rosterStats accuracy:** Currently hardcoded per visa type. Production would need real backend data.

### Known Tradeoffs
- **Static expert pool:** 3 hardcoded experts for avatars. Production would rotate from a larger set.
- **Hardcoded rosterStats:** Attorney counts and case numbers are static per visa type. Production would pull from real data.
- **No real matching backend:** The roster panel is purely presentational — no actual routing to a specific attorney.
- **Case assessments are pre-written:** All 35 are static. A real system could use the free-text detail to generate more personalized assessments.
- **Single-file architecture:** Everything (CSS + HTML + JS + data) is in one HTML file for prototype simplicity. Would need componentization for production.

---

## Changelog
- **2026-03-08:** Created initial flow document from current implementation state.
- **2026-03-08:** Replaced fake testimonials with 4 real Trustpilot immigration reviews (incl. one 4-star). Added Trustpilot 4.8 rating badge.
- **2026-03-08:** Reframed price ($65 today + membership as bonus), added price anchoring ($300–500/hr), Trustpilot in hero/match/payment, removed "14" from attorney count.
- **2026-03-08:** Added sticky mobile CTA bar on landing page. Merged urgency into match screen (3 intake steps → 2, 7 screens → 6).
- **2026-03-09:** Replaced fake experts (Jessica B., Richard V., Neil B.) with real JustAnswer attorneys (Guillermo S., Judith L., Denise C.). Redesigned match screen from single-expert card to roster panel with per-visa-type stats, stacked avatars, "+N more" badge, stats grid, and "why this matters" bar. Updated payment strip and confirmation to use stacked avatars with generic messaging. Removed `expertCaseStats` (replaced by `rosterStats`).
