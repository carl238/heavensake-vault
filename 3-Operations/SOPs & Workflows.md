---
type: knowledge
source: carl-claire-37-calls
status: validated
last-updated: 2026-03-25
tags: [SOPs, workflows, operations, content-machine, whale-hunt, restaurant-collab, newsletter, landing-page, communication]
---

# SOPs & Workflows

Operational standard operating procedures extracted from HEAVENSAKE source documents. These are the working methods Carl has mandated across all team functions. "Creativity without systems is useless." — Carl Hirschmann

---

## 1. "AI Content Machine" SOP — Content Generation

The master workflow for producing all brand-aligned content using AI assistance.

**Step-by-step:**

1. **Capture** — Record all meetings using [[Fireflies]].
   - *Operational Rule:* Always extend calendar invites by **1 hour** to prevent Fireflies from dropping off early and missing data.

2. **Centralize** — Upload raw audio, Fireflies transcripts, Q&As, and daily voice notes into a dedicated [[NotebookLM]] "brain."

3. **Master Prompt Generation (Phase A)** — Speak directly into [[Gemini]] using the Whisper voice feature with raw context to generate a highly detailed "Master Prompt."

4. **Execution (Phase B)** — Open a fresh [[Gemini]] chat, paste the Master Prompt, and attach the [[NotebookLM]] source document. This forces the LLM to filter generic ideas and output brand-specific ("precision branding") results — no generic AI fluff.

**Why it works:** The NotebookLM source acts as a brand firewall — any AI output that contradicts the vault gets filtered. The Whisper voice feature allows rapid context injection without typing.

---

## 2. "Whale Hunt" — Customer Audit Workflow

The E-Commerce Customer Audit Workflow for identifying and converting the Top 20 VIP customers.

**Step-by-step:**

1. Export the [[Shopify]] customer list.
   - *Access Protocol:* Requires 2-step verification from Kevin's email (Admin account). Time-sensitive — coordinate in advance.

2. Combine standard **RFM data** (Recency, Frequency, Monetary) with **AI-driven external enrichment**:
   - Python-based identity searches across [[LinkedIn]] and [[Instagram]]
   - Identify C-suite executives, finance executives, surgeons, media figures

3. Tag **"diamonds in the rough"** — customers with high external influence/wealth but low initial spend.

4. Execute **1-to-1 personalized cold email outreach**, referencing each customer's recent LinkedIn awards, media quotes, or Instagram posts.
   - Example: "I read your article in Forbes — congratulations. I wanted to share something we've been working on..."

5. Escalate top prospects to [[Club Heaven]] concierge care pathway ($5,000 annual membership).

**Current baseline (see [[Conflicts for Carl to Resolve]] for reconciliation):** ~315 purchasing customers; top 20 customers (not top 20%) identified as priority.

**Owner:** [[Gloria]] (CRM/Data Specialist) with AI tooling support.

---

## 3. Social Media "Boost" Triage SOP

Rules for deciding which posts to pay to boost, and how to evaluate performance.

**Core Rule:** Never evaluate organic performance solely on "likes."
- A **like** = a "handshake"
- A **save** = "an invitation into the home"
- **Only boost** posts that exhibit a high **Save-to-Engagement ratio**

**Meta Reporting Rule:**
- Do NOT accept default Ads Manager performance views (which focus on reach)
- Custom reports must manually check:
  - Post saves
  - Profile visits
  - 100% video plays
- If Jakub (or any agency) sends a report without these metrics, it is incomplete and should be rejected

---

## 4. Restaurant Collaboration SOP (Three-Tier System)

Three-tier system for allocating digital support to restaurant partners. Final tier assignment is always Carl's call — the framework is a proposal, not automatic. (Call 32)

**Tier 1 (Premium — Zuma/ICA level):**
- Custom co-branded graphics
- Professional photos + videos (pre- and post-event)
- Dedicated landing page on heavensake.com
- Featured/collab post
- Paid social ($350 for 7 days / $50/day suggested start)
- Analytics reports on Meta ads

**Tier 2 (Standard):**
- Standard co-branded graphics (no video)
- Landing page on heavensake.com (no paid ads)
- Basic guidance for social posts
- Shareable content for partner channels

**Tier 3 (Basic):**
- No landing page
- Basic co-branding only
- Reposts on HEAVENSAKE stories ONLY

**The principle:** The brand's digital resources are finite. The most culturally impactful partners get the most support. **Tier assignment is determined by Carl.**

---

## 5. Newsletter Template Rules (80/20)

**Format mandate:**
- **80% brand value (stories, content, craft) / 20% commercial/sales**
- **80% Text / 20% Visual** (one high-quality photo maximum)
- HTML-heavy, image-embedded buttons are **BANNED** — they require constant developer intervention and look too commercial
- Text must be editable HTML (not baked into a JPEG)

**Content philosophy:**
- Must deliver actual value to the customer — not brand self-celebration
- Newsletter subject lines: "Reviving an Icon" approved framing
- No discounts — deliver exclusive access, knowledge, or scarcity instead

---

## 6. Landing Page Templates

Two core templates needed on heavensake.com:

**Events LP (High-Friction — Lead Generation):**
- Email capture gate — tease exclusive info (menu, DJ, event details) in exchange for email
- Designed to **gatekeep** information
- Goal: Lead generation
- Used for: Monaco F1 party, members-only drops, event RSVPs

**Product LP (Low-Friction — Conversion):**
- Checkout page for limited-edition releases, special drops, merch
- Designed purely for **conversion**
- Must allow customers to discover the full collection without dead-ends
- Goal: Direct purchase / waitlist completion
- Used for: Sakura Prestige lottery, Hanami drop, Club Heaven membership

**Website infrastructure target:** CMS templated so pages can be duplicated and edited without full rebuild. Target: ~$300 and 3 days per new landing page. (Call 32)

---

## 7. Blog Rules

- Always ordered newest-to-oldest. Publication dates must appear on all articles. (Calls 30, 31)
- Content structure: dramatic hero image → narrative text + image blocks → luxury context moments + product shots
- Carl personally reviews and refines blog copy before it goes live (Call 31)

---

## 8. Communication Rhythm

**Daily:**
- **6pm WhatsApp report:** From [[Claire Senda]] to Carl — digestible, prioritized by importance, with links to outputs. (Call 12)
- Morning updates: What's been done, current blockers, ideas. "What works best for me is to wake up and have an understanding of what is happening out there with my team." (Call 30)

**Weekly:**
- **Weekly goals:** Define 3–4 clear goals at the start of each week. (Call 26)
- **Monday team call:** Align EU team (Gloria, Giancarlo, Claire, Carl) before US marketing call. (Call 26)
- Weekly progress updates are a baseline expectation — not just when asked.

**Meeting structure:**
| Meeting | Frequency | Participants | Purpose |
|---------|-----------|-------------|---------|
| Weekly Marketing Alignment | Weekly (Monday) | Carl, Claire, Gloria, Digital | Campaign updates, content decisions, priorities |
| US Sales / Marketing | Weekly | Carl, Zak, Cesar, Nes | US market execution |
| Carl + Claire catch-up | 2–3x/week | Carl, Claire | Brand direction, content approval |
| Financial review | Monthly | Carl, Sebastien, Maurizio | Budget vs. actuals, adjustments |

---

## 9. Communication Protocol — Brewery Partners

| Scenario | Contact |
|----------|---------| 
| Routine operational matters | [[Nana]] (front-facing) |
| Pricing / commercial / strategic | [[Sebastien L'Hermitte]] (escalation) |
| Relationship-critical or crisis | [[Carl Hirschmann]] (personally) |
| Sample logistics / US market | [[Zak Gross]] |

**Cultural note:** Japanese business relationships require consistency, face-saving, and clear communication. When something goes wrong, the fix must be private, fast, and never cause public embarrassment.

---

## 10. Vendor Management Protocol

Before commissioning any vendor:

1. **Agree on exact deliverable, budget range, and specification/profile** before any research or sourcing task. (Call 33)
2. **Get written confirmation** for all operational and legal decisions. "I need these things in writing and I should have them already today." (Call 33)
3. **Test bit by bit** — never scale a vendor before they've proven themselves on small tasks.
4. **Grill with specific questions** — use AI to generate trick questions for vendor evaluations. (Call 28)
5. **Watch for "pro hustlers"** who use AI to sound smarter in meetings. (Call 28)
6. **Document all communications** with problematic vendors (especially A2J) for potential legal review.

---

## 11. AI Tool Usage Protocol

| Tool | Use Case |
|------|---------|
| **Gemini** | Research queries, strategy thinking partner, technical questions before vendor calls |
| **ChatGPT** | Midjourney prompt creation, customer list analysis, research |
| **Claude** | Copywriting/refinement |
| **Midjourney / Nano Banana Pro** | Image generation and AI editing/refinement |
| **Perplexity** | Influencer research, specific factual research |

**AI use principle:** "I want people to use [AI]. What I do not want is people to just put the PDF into the thing, say give me your feedback, and then copy paste the answer without really having in depth understood the answer." (Call 28)

Use AI as a first step, not as a final answer. Always understand the output.

---

## 12. Shopify / Tech Stack Access Protocol

| System | Owner | Access Notes |
|--------|-------|-------------|
| [[Shopify]] (US) | CIPSE / Tipsy | Admin via "Kevin's account"; requires live 2-step verification code sent to Kevin's email |
| [[Klaviyo]] | Internal | Primary email platform (migrated from HubSpot) |
| [[HubSpot]] | Internal | CRM — multi-user access and authenticator app needed. (Calls 1, 2, 5) |
| [[Google Analytics 4]] + [[GTM]] | Active on site | Pixel migration in progress |
| [[Meta Business Suite]] | External | Ad account + pixel being migrated back to HEAVENSAKE ownership |
| [[Notion]] | [[Abdel Giant Nerd]] | Central operating system; stores processes, supply chain |

---

## Related Notes

- [[Carl's AI Thesis]]
- [[Meta Ads Strategy]]
- [[Team Structure & Roles]]
- [[Carl's Leadership Philosophy]]
- [[Legal & Compliance]]
- [[Conflicts for Carl to Resolve]]
