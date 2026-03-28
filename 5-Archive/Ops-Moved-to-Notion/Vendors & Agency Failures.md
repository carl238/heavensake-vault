---
type: knowledge
source: notebooklm-extraction
status: validated
last-updated: 2026-03-25
tags: [vendors, agencies, failures, A2J, Garden, Coronito, Jakub, Studio-Magla, lessons-learned]
---

# Vendors & Agency Failures

A documented record of vendor and agency failures — maintained as institutional memory so the same mistakes are not repeated. Carl's rule: the internal team must use AI to double-check every external vendor before payment or delivery is accepted.

---

## A2J / Auto J — Japanese Web Agency

**Relationship:** Japanese tech/web agency hired to handle the Japanese e-commerce launch.

**Failures documented:**

1. **Pricing abuse:** Charged approximately **$3,000** for what was essentially a landing page template. Carl deemed this "too expensive for a simple page."

2. **Velocity failure:** Custom forms took **2–3 weeks** (quoted at €600–€1,000) to produce. The agency operates on extremely slow execution cycles incompatible with HEAVENSAKE's pace.

3. **Domain launch failure:** Launched the new HEAVENSAKE website on a **subpage** instead of the main domain — a fundamental technical error.

4. **Translation failure:** Internal translators produced poor-quality Japanese copy that the HEAVENSAKE team could not understand and that did not reflect the brand voice.

5. **Project management void:** When [[Garden]] (the PM company) exited, A2J was left without a project manager, causing severe delays and untracked communication across all open workstreams.

**Status:** Relationship under review / de-prioritized. All future Japanese web work must have internal oversight.

---

## Garden — Project Management (Fallout)

**Relationship:** The original project management company that HEAVENSAKE contracted to oversee the Japanese digital/web operations.

**What happened:** HEAVENSAKE had a complete fallout with Garden. When Garden exited, they left [[A2J]] without a project manager — creating a vacuum that caused months of delays, lost communication threads, and untracked work.

**Key lesson:** Never let an external agency fully control the PM layer for a critical workstream. HEAVENSAKE must maintain an internal point of contact with full visibility into all vendor projects, regardless of who is managing day-to-day execution.

**Status:** Relationship terminated.

---

## Coronito — Prestige Landing Page Disaster

**What happened:** Coronito was engaged to build an intermediary landing page for the Prestige product launch.

**Cost:** **$7,000–$8,000**

**Carl's verdict:** "A disaster." The page failed to meet brand standards and did not justify its cost.

**Key lesson:** No external vendor should be paid premium rates for a single landing page. With current AI tools ([[Perplexity Computer]], [[Gemini]]), Carl personally demonstrated the ability to reprogramme pages in-house. The $7–8K should have been used for campaign spend, not production.

**Status:** Relationship terminated. The Coronito page is no longer in use.

---

## Jakub Cambor — AI-Generated Reports & Inflated SEO Data

**Relationship:** [[Jakub Cambor]] — Freelance paid media, AI automations, and SEO consultant. Operates as "AI for Marketing" (aiformarketing.co.uk).

### Incident 1: Meta Ads Report (Late 2025)

Carl used [[Gemini]] to audit Jakub's agency report and discovered:
- Facebook actually offers **~500 exportable data criteria** — Jakub's report covered only a fraction of these
- The report was "only 70% precise" — missing essential performance data
- Carl deduced that Jakub was likely using an LLM (AI) to generate his strategy, effectively charging the brand **$350 for 2 hours of automated AI output** with no original analysis

**The specific incident:** Jakub submitted a report claiming campaign "EA1" (paid boost) performed best. Carl manually checked the Instagram app and saw the organic "Sabbes" post had 3,500 likes and 21 comments, while "EA1" had only 422 likes and 1 comment. The agency's Ads Manager metrics were cherry-picked from a non-customized view.

**Broader revelation:** This incident crystallized Carl's rule that the internal team must use AI to double-check every external vendor's output before accepting it. "If Gemini can catch what Jakub missed in 3 minutes, there is no excuse."

**Impact on Paid Ads approach:** Led to the [[Social Media Boost Triage SOP]] and the mandate for custom Meta reporting (saves, profile visits, 100% video plays — not default reach metrics).

### Incident 2: SEO Audit Report (March 2026)

Jakub delivered a full SEO audit (£650) and keyword research spreadsheet. Perplexity Computer cross-referenced every claim against the live site and DataForSEO actuals.

**What was found:**
- Report is ~70% accurate — most technical diagnoses are correct
- Heavily AI-generated: the assembly likely cost ~$10 in DataForSEO API calls
- Keyword volume data had 4 significant inflation errors ("sake food pairing" reported as 1,900 — actual volume: 170)
- The report contains an internal contradiction: states "no Product schema" in one section, then recommends "maintaining" it in another — copy-paste from the AI template
- Claimed "zero lazy loading" — verified as false; Dawn v15.4.0 implements it natively
- Projected 10-20x growth to create urgency for his ongoing retainer proposal

**Financial structure exposed:**
- Step 1: Audit (£650) — $10 in API costs, AI-assembled
- Step 2: Technical fix proposal (£1,500) — covers items Carl and Perplexity Computer fixed in one session at zero cost
- Step 3: Ongoing monitoring (£1,500/month → negotiable to £800) — monthly DataForSEO reports (~$10/month in API costs)
- Total Year 1 if fully bought: ~£14,150. Total data cost: ~£100.

**Verdict:** Pay the £650 invoice — the audit was legitimate work. Do not pay for technical fixes (done). Negotiate monitoring to £800/month or use Giancarlo's Semrush access instead.

**Useful deliverables to keep:** Seasonal data (gift sets spike 11x in December), competitor keyword intersection (97 keywords overlapping with Tippsy).

---

## Studio Magla — Milan Design Agency

**Relationship:** [[Studio Magla]] — Milan-based design agency handling the 10-Year Anniversary visual systems and campaigns.

**What is documented:**
- Active as of March 2026 for the 10-Year Anniversary visuals
- Carl has expressed concern about them being "B-players"
- The team was reportedly unable to duplicate a blog post on the CMS without charging extra fees — causing operational friction and delays

**Outstanding question:** Whether Studio Magla was retained for the full 10-Year Anniversary campaign or released. **NOT IN SOURCES.** This is flagged as an open question in [[Contradictions & Open Questions]].

**Current status:** Unclear. Monitor for resolution.

---

## Broader Vendor Management Principles (From Carl)

Carl's rules for all vendor relationships, derived from these failures:

1. **AI-audit all deliverables.** Before accepting any agency report, strategy document, or creative asset — run it through Gemini, Perplexity, or equivalent. If the AI finds gaps in under 3 minutes, the vendor is not adding value.

2. **Never let a vendor own the PM layer.** HEAVENSAKE must always have internal project visibility, even when external PMs are contracted.

3. **Price is not quality.** Coronito's $7–8K landing page was a disaster. Carl built a better solution himself. Agency premium does not equal premium output.

4. **Slow execution is non-negotiable.** A2J's 2–3 week form-build timeline is incompatible with a brand that operates on cultural momentum. Any vendor who cannot move in 24–48 hours on a clear brief is not the right partner.

5. **Outcome-based compensation only.** Flat fees create misaligned incentives. All future vendor agreements should tie compensation to measurable outcomes (leads, sales, saves, conversion rate improvements).

---

## Related Notes

- [[SOPs & Workflows]]
- [[Contradictions & Open Questions]]
- [[Carl's AI Thesis]]
- [[Team Structure & Roles]]
- [[Carl's Lessons Learned]]
