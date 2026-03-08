# Directive: Mini Javatar Landing Page Build (GitHub Pages)

**Date:** March 6, 2026  
**Owner:** Vishal Dhanuka  
**Purpose:** Build 3–4 sample Mini Javatar landing pages, host on GitHub Pages, to demonstrate the concept and test conversion patterns.

---

## Background: What is a Mini Javatar?

**JustAnswer** is an on-demand expert Q&A platform ($150–200M revenue, 21M monthly visitors). Users pay $40–60/month for unlimited expert access across 150+ topics: doctors, lawyers, vets, mechanics, accountants, etc.

**Javatars** are JustAnswer's vertical-specific sister brands — standalone microsites sharing JA's backend but with niche branding:
- `askadoctor.help` (Medical)
- `askalawyeroncall.com` (Legal)
- `askaveterinarianonline.com` (Veterinary)
- `taxexpertnow.com` (Tax)
- `carmechanic.expert` (Auto)

**Mini Javatars** go one level deeper — hyper-niche brands targeting specific sub-verticals. Same backend (Pearl AI intake → expert match → subscription billing), different front door: domain, branding, landing page design.

**Business thesis:** The only thing that changes is the landing page. Everything else is JustAnswer infrastructure. So each Mini Javatar is a 1–2 week launch, not a platform rebuild. Build → Test → Validate → Scale.

### Why it works
- **SEO:** `divorcelawyer.help` outranks `justanswer.com/family-law` for niche queries
- **Trust:** Users searching "ask a dermatologist" convert better on a dermatology-branded page
- **LTV:** Niche users (immigration law, tax resolution) have higher willingness to pay
- **Speed:** JA's entire advantage over competitors is instant expert access (competitors take hours/days - JA is minutes)

---

## The 4 Landing Page Templates

**Critical:** The template must match the user's emotional state. A mismatch kills conversion.

### Template A — "My Hair is on Fire" 🔥
- **User mindset:** Panic. Need help NOW. Not shopping — desperate.
- **Examples:** Dog ate chocolate, kid has weird rash, just got served divorce papers, just got fired, IRS letter arrived
- **What converts:**
  - Minimal page — one powerful line of copy
  - Chat box front and center, above the fold
  - "Expert available now" with green live dot
  - Zero friction (no long forms, no pricing tables)
  - Mobile-first (these queries happen on phones)
- **Anti-pattern:** Long testimonials, feature lists, pricing comparison — users bounce
- **Design feel:** 911 dispatcher page. Fast, clinical, reassuring.

### Template B — "I Need Someone I Can Trust" 🎓
- **User mindset:** High stakes, high emotion. Must trust the expert before engaging. Not in crisis — making an important decision.
- **Examples:** Immigration case, divorce proceedings, employment discrimination, estate planning
- **What converts:**
  - Expert credentials prominent (photos, credentials, years of experience)
  - Specificity: "Talk to a licensed immigration attorney who handles H-1B and green card cases"
  - Testimonials from people in similar situations (not generic)
  - Guided intake form that asks smart/specific questions before matching
  - Trust signals: verified credentials, review counts, professional bodies
- **Anti-pattern:** Generic "ask an expert" framing — they need to know this expert handles *their specific* problem
- **Design feel:** Expert showcase → guided intake questionnaire → match to expert

### Template C — "Is This Normal?" 🔍
- **User mindset:** Uncertain, possibly anxious, still researching. May not know they need an expert. Looking for context before committing.
- **Examples:** Skin condition, pet behavior change, mental health question, weird car noise, unusual symptom
- **What converts:**
  - Content-first page with brief educational context that mirrors their concern
  - Photo/file upload ("Upload a photo of your skin — a dermatologist will review it")
  - Guided symptom questionnaire that builds understanding, then transitions to expert chat
  - Soft CTA — "Get an expert opinion" not "Buy now"
- **Anti-pattern:** Jumping straight to chat — they need to feel understood first
- **Design feel:** Symptom checker / guided questionnaire → summary → expert consultation CTA

### Template D — "Clock is Ticking" ⏰
- **User mindset:** Deadline-driven. A specific date or consequence creates urgency. They know they need help but have been procrastinating.
- **Examples:** Tax filing deadline, court date approaching, lease expiring, insurance claim window, visa expiry
- **What converts:**
  - Countdown or deadline emphasis ("Tax Day is in 47 days — file with a CPA now")
  - Calculator or estimator that quantifies the problem ("What's the penalty if you miss?")
  - Specific, action-oriented CTA tied to the deadline
  - Urgency without panic — authoritative, not scaremongering
- **Anti-pattern:** Evergreen messaging — urgency is the entire hook
- **Design feel:** Deadline countdown + calculator + expert CTA

---

## Recommended Landing Pages to Build (3–4 Examples)

Pick one example per template type (or the top 3 if building 3 pages). These are the highest-priority Mini Javatar picks, matched to their templates:

### 1. Dog Vet Emergency — Template A 🔥
- **Domain idea:** `dogvet.help` or `askadogvet.com`
- **Niche TAM:** ~$1.2B (pet telehealth)
- **User query:** "my dog ate chocolate", "dog won't stop vomiting", "dog has seizure"
- **Hero copy ideas:**
  - "Your dog needs a vet. Right now."
  - "A licensed vet is online and ready. No appointment needed."
  - "Is [pet name] going to be okay? Ask a vet now — answer in minutes."
- **Key UI elements:** Breed selector (optional), chat input above fold, green "Vet Available Now" dot, mobile-first
- **Competitors this beats:** Vetster ($30–75/video consult, scheduling required), Pawp ($24/mo, async)
- **JA advantage:** Largest vet network, instant chat, no scheduling

### 2. Immigration Lawyer — Template B 🎓
- **Domain idea:** `immigrationlawyer.help` or `askimmigration.expert`
- **Niche TAM:** ~$2.4B (US immigration legal services)
- **User query:** "H-1B denial", "green card questions", "DACA renewal", "visa interview tomorrow"
- **Hero copy ideas:**
  - "Talk to an immigration attorney today. No appointment. No retainer."
  - "Got an RFE? Visa denied? An immigration lawyer can help right now."
- **Expert showcase:** Show 2–3 attorney profiles with bar admission, case types (H-1B, family petition, asylum), years of practice
- **Trust signals:** Verified bar numbers, review counts, "Available now" status
- **Intake flow:** "What visa type are you dealing with?" → "What's your specific situation?" → match to attorney
- **Competitors this beats:** Boundless (days for feedback), Avvo (async, hours wait), VisaNation ($1,500–5,000, phone only)
- **JA advantage:** Instant live chat with vetted immigration attorney — nobody else offers this

### 3. Ask a Dermatologist — Template C 🔍
- **Domain idea:** `askadermatologist.com` or `skinexpert.help`
- **Niche TAM:** ~$48B (dermatology market)
- **User query:** "is this mole normal", "weird rash photo", "what is this skin thing"
- **Hero copy ideas:**
  - "Upload a photo of your skin. A dermatologist will review it."
  - "Is that mole normal? A board-certified dermatologist can tell you — today."
- **Key UI elements:** Photo/file upload widget front and center, guided symptom input ("Where is it?", "How long has it been there?", "Has it changed?"), soft CTA
- **Competitors this beats:** FirstDerm ($29/consult, 24hr wait), DermatologistOnCall (scheduling required)
- **JA advantage:** Chat is faster than any async photo review competitor

### 4. IRS / Back Tax Help — Template D ⏰
- **Domain idea:** `irshelp.expert` or `backtaxes.help`
- **Niche TAM:** ~$14B (tax resolution market)
- **User query:** "got IRS letter", "owe back taxes", "IRS audit help", "tax deadline", context-specific near April 15
- **Hero copy ideas:**
  - "Got a letter from the IRS? Find out what it means — in minutes."
  - "Tax Day is April 15. A CPA can file an extension or fix your problem today."
- **Key UI elements:** Countdown timer to April 15 (if seasonal), "What type of IRS notice did you receive?" dropdown (CP2000, CP503, audit letter, etc.), penalty calculator, authority-forward CTA
- **Competitors this beats:** Optima Tax Relief ($250+), TaxReliefCenter ($350+) — JA is 10× cheaper for guidance
- **JA advantage:** Immediate access at a fraction of tax resolution firm cost

---

## Technical Requirements

### Hosting: GitHub Pages
- Each landing page is a **single self-contained HTML file** (inline CSS + JS, no build step required)
- Organize as:
  ```
  /docs/
    index.html              ← optional hub/index
    dog-vet/
      index.html
    immigration-lawyer/
      index.html
    ask-a-dermatologist/
      index.html
    irs-help/
      index.html
  ```
- Enable GitHub Pages from `/docs` folder → automatically served at `https://{user}.github.io/{repo}/`
- Each page should have its own Open Graph tags, meta description, and title for shareability

### Technology Constraints
- **No frameworks, no npm, no build step.** Pure HTML/CSS/JS only.
- Use modern CSS (custom properties, flexbox, grid, clamp() for fluid type)
- Copy aesthetic and color system from `outputs/mini_javatar_pitch.html` (which already exists in this workspace as a reference)
  - Background: `#f0f5ff`, Surface: `#ffffff`, Accent: `#0066bb` / `#2563eb`, Text: `#1a2f5e`
- Mobile-first responsive — these users are on phones
- No external API calls — chat/intake is simulated UI only (placeholder CTA that would link to JA's Pearl AI intake in production)
- Fast load — aim for under 50KB per page (inline everything)

### UX Requirements Per Template
- **Template A (Panic):** Above-fold chat input or big CTA button. Green "Available Now" dot. Expert count or wait time. Minimal copy. Works on 375px screens.
- **Template B (Trust):** Expert profile cards. Guided intake steps (multi-step, not one long form). Progress indicator. Credential/badge display.
- **Template C (Uncertain):** File-upload widget (visual only, no actual backend). Symptom checklist or guided questions. Soft, reassuring copy. "Get an opinion" not "Buy now."
- **Template D (Deadline):** Live countdown timer (JS, client-side). Calculator widget (e.g., penalty estimator). Bold deadline-anchored copy. Authoritative but not scary.

---

## Existing Reference: The Pitch Deck

A polished HTML slide deck already exists at `outputs/mini_javatar_pitch.html`. Study its:
- Color system and CSS variables
- Typography scale
- Card/surface aesthetics
- Badge components

This should be the visual foundation — Mini Javatar landing pages should feel like they come from the same brand family.

---

## What "Success" Looks Like

These pages are **demos / proof-of-concept**, not production. Success means:
1. Each page clearly communicates the value prop for that niche
2. The template pattern (A/B/C/D) is visibly different across pages
3. Anyone viewing the pages immediately understands what Mini Javatars are
4. The pages could plausibly be shown to stakeholders as what a real landing page would look like
5. Hosted and accessible via a public GitHub Pages URL

---

## Files Already in This Workspace (For Reference)

| File | What's in it |
|------|-------------|
| `outputs/mini_javatar_pitch.html` | **PRIMARY REFERENCE** — Polished slide deck. Use its CSS variables, component style, and design language as the visual foundation. |
| `directives/mini_javatar_strategy.md` | Full strategy: 4 templates (A/B/C/D) with detailed design guidance, deployment strategy, 10 Mini Javatar picks with template assignments. |
| `outputs/mini_javatar_opportunities.md` | 20 Mini Javatar candidates (Tier A/B/C) with TAM, WTP, urgency scores, domain ideas. |
| `outputs/competitive_landscape.md` | 10-vertical competitive analysis — what competitors do on their landing pages, what works, what JA should steal. Read the "Mini Javatar Steal" section per vertical. |
| `outputs/demand_landscape.md` | Consumer demand research, pain point statistics, workaround behavior. Useful for writing copy. |
| `agents.md` | How this agent system works (3-layer architecture: directives → orchestration → execution scripts). |

---

## Suggested Build Order

1. **Read** `outputs/mini_javatar_pitch.html` fully — extract the CSS vars and component patterns
2. **Build Template A** — Dog Vet Emergency (simplest: minimal copy + big CTA)
3. **Build Template B** — Immigration Lawyer (expert cards + intake flow)
4. **Build Template C** — Ask a Dermatologist (photo upload UI + guided symptom questions)
5. **Build Template D** — IRS / Back Tax Help (countdown timer + penalty calculator)
6. Create a simple `index.html` hub that links to all four pages
7. Set up GitHub Pages hosting

Each page should take ~1 hour to build. Do not over-engineer. These are demos.

---

## Changelog
- 2026-03-06: Created. Context brief for landing page build session. Covers Mini Javatar concept, 4 templates, 4 specific page specs, tech requirements, and build order.
