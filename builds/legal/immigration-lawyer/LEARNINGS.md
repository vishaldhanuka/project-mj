# Immigration Lawyer Landing Page — Learnings & CRO Insights

> Reference document from expert funnel review (March 2026)
> **Page:** `builds/legal/immigration-lawyer/index.html`

---

## Expert Review Summary

**Grade: B+** — Strong funnel architecture for paid search. Key gap is pricing psychology, not UX.

---

## What's Working Well

1. **Case assessment on match screen** — Giving before asking. The personalized paragraph (35 unique, 7 visa types × 5 situations) proves the system understood the user's problem. This is the single best conversion driver in the funnel.
2. **Single matched expert (not a picker)** — **Evolved to roster panel.** Originally we showed one matched expert to remove decision friction. However, this was misleading since the specific expert might not be available when the user connects. The new roster panel (“23 immigration attorneys have helped people with cases like yours”) provides credibility through team volume + per-visa-type stats without promising a specific person. Stacked avatars with a “+N more” badge show real people while being honest about the team-based model.
3. **Situation-aware consultation plans** — Payment screen shows 3 case-specific items (e.g., "Review your denial notice and identify grounds for appeal") + 2 generic. This justifies the price with concrete deliverables.
4. **Intake progression** — 3 steps (visa type → situation → urgency) is well-sequenced. Each step correctly narrows the problem. Labels like "My H-1B petition was denied" are in the user's language.
5. **Trust infrastructure** — Real JustAnswer expert photos with verified credentials (JD, bar admissions, actual case counts from profiles), BBB/Trustpilot/DigiCert badges, "cancel anytime" placement all reduce anxiety at the right moments. Replaced fake experts with real attorneys: Guillermo S. (122K+ helped, 18 yrs), Judith L. (48K+ helped, 18 yrs), Denise C. (3.7K+ helped, ★4.9).

---

## Critical Issues Identified

### 1. Subscription Framing Is Wrong
**Problem:** "$65/month membership" frames this as a recurring commitment. Users arriving from Google Ads have a specific problem — they want a consultation, not a relationship.

**Impact:** Subscription framing triggers commitment anxiety ("what if I forget to cancel?") at the exact moment you need purchase confidence.

**Fix:** Reframe as consultation purchase:
- Change "$65/mo — cancel anytime" → "Your consultation: $65 today"
- Position the membership as a bonus: "Includes 30-day membership — ask unlimited follow-up questions"
- User mentally pays for the consultation (solving their problem) and gets ongoing access as a bonus
- **Expected lift: +15–25% payment screen conversion**

### 2. "14 Attorneys" → 3 Experts → Only 2 Match = Trust Time Bomb
**Problem:** Hero badge said "14 Immigration Attorneys Online Now" but the system only had 3 experts, and only 2 ever matched. If a user encounters the page multiple times or talks to friends, credibility collapses.

**Resolution:** Three-part fix:
1. Removed specific count from hero badge → "Immigration Attorneys Online Now"
2. Replaced single-expert match card with **roster panel** showing per-visa-type team stats (e.g., "23 immigration attorneys have helped people with cases like yours")
3. Replaced fake experts entirely with real JustAnswer attorneys (Guillermo S., Judith L., Denise C.) using real photos, verified case counts, and real ratings

**Status:** ✅ Fixed

### 3. No Price Anchoring Anywhere
**Problem:** $65 appears with zero reference point. Immigration firms charge $300–500/hr. Without anchoring, $65 is evaluated against "free" (Google searches, Reddit, forums) rather than against the real alternative.

**Fix:** Add anchoring on match and/or payment screens:
- Match screen: "Immigration consultations typically cost $300–500/hr"
- Payment screen: subtle crossed-out comparison or "vs. $350/hr average"
- **Expected lift: +10–20% payment conversion**

---

## Questionable / Debatable Decisions

### 7 Screens May Be Too Many for Paid Search
Users from Google Ads are high-intent. ~~7 screens (landing → intake-1 → intake-2 → intake-3 → match → pay → confirmation) could cause drop-off.~~ **Resolved: Now 4 screens.** Pearl chat replaced intake-1, intake-2, and match with a single conversational interface. Flow: Landing → Chat → Payment → Confirmation.
- **Expected lift from merge: +5–10% intake completion** → actual reduction is even larger (3 screens merged into 1).

### All 3 Testimonials Are 5-Star
Every testimonial being 5 stars signals "curated" or "fake" to skeptical users. One 4-star review with a minor critique builds more trust.
- **Fix:** Replace one 5-star with a realistic 4-star review → DONE (replaced with real Trustpilot reviews including 4-star)

### Step 2 "Continue" Always Enabled
The situation selection step allows proceeding without selecting. This means some users reach match with no situation data, producing a generic assessment. Consider requiring selection.

### Sub-brand Trust Gap
"askalawyeroncall.com" is not a recognized brand. The footer says "Powered by JustAnswer" but it's buried. Consider making the JustAnswer association more prominent in the hero area.

---

## Recommendations (Ranked by Expected Impact)

| # | Change | Expected Impact | Effort | Status |
|---|--------|----------------|--------|--------|
| 1 | Reframe price as consultation purchase | +15–25% payment conversion | Low | ✅ Done |
| 2 | Add price anchoring ($300-500/hr comparison) | +10–20% payment conversion | Low | ✅ Done |
| 3 | Add sticky mobile CTA bar on landing | +8–15% landing-to-intake | Medium | ✅ Done |
| 4 | Merge urgency into match screen (-1 screen) | +5–10% intake completion | Medium | ✅ Done |
| 5 | Fix "14 attorneys" credibility gap | Risk mitigation | Low | ✅ Done |
| 6 | Add one 4-star testimonial for realism | Credibility lift | Low | ✅ Done (real Trustpilot reviews) |
| 7 | Replace fake experts with real JustAnswer attorneys | Trust + credibility | Medium | ✅ Done (Guillermo S., Judith L., Denise C.) |
| 8 | Roster panel instead of single-expert match | Honest framing + credibility | Medium | ✅ Done (per-visa-type stats, stacked avatars, "+N more" badge) |
| 9 | Stats grid on match screen (cases, quarterly, rating, response) | Quantified trust | Low | ✅ Done |
| 10 | "Why this matters" trust bar | Verified credentials, speed, confidentiality | Low | ✅ Done |
| 11 | Replace multi-screen intake with Pearl chat | -3 screens, CTA-promise alignment, less drop-off | Medium | ✅ Done (simulated Pearl chat) |

---

## Message-Market Match Analysis

**User state when landing (from Google Ads):**
- Has a specific immigration problem (H-1B denial, green card question, etc.)
- Anxious, possibly confused by legal complexity
- Looking for authoritative guidance, not a subscription service
- Price-sensitive but willing to pay for expert help (just searched for it)

**What the page promises:** Matched expert, personalized assessment, fast response
**What the page delivers:** Case assessment that proves understanding + clear consultation plan

**Gap:** The promise-to-delivery chain is solid UNTIL the payment screen, where "membership" framing contradicts the consultation the user came for.

---

## Trustpilot Data (for reference)

- **Rating:** 4.8 / 5
- **Total reviews:** 11,237
- **Distribution:** 92% 5-star, 5% 4-star, <1% 3-star, <1% 2-star, 2% 1-star
- **#13** in Legal Services category
- **#1** in General Practice Attorney
- **Source:** trustpilot.com/review/www.askalawyeroncall.com

### Immigration-Specific Reviews Used on Page
See `FLOW.md` → Testimonials section for the selected reviews and their sources.

---

### "Describe Your Case" CTA Disconnect — Resolved
**Problem:** The hero CTA said "Describe Your Case" but led to radio-button selectors with an optional textarea and a pre-generated summary. Users never actually described their case in a meaningful way.

**Insight:** The landing page's job isn't to BE Pearl — it's to get someone from Google Ads INTO Pearl with trust built up and context pre-loaded. Landing page does: trust-build, pre-qualify, justify price. Pearl does: actual conversation.

**Resolution:** Replaced the 3-screen intake+match flow with a simulated Pearl chat interface. Users now literally describe their case in a conversational UI. For production, this simulated chat would be replaced by embedding the actual Pearl chat.

---

## Changelog
- **2026-03-08:** Created from expert CRO review findings.
- **2026-03-08:** Marked recommendation #6 as done (real Trustpilot reviews integrated).
- **2026-03-09:** Replaced 3-screen intake+match flow with simulated Pearl chat. Reduced from 7 screens to 4 (Landing → Chat → Payment → Confirmation). Added recommendation #11. Updated "7 Screens" tradeoff as resolved. Added "Describe Your Case" disconnect insight.
