---
type: knowledge
source: notebooklm-extraction
status: validated
last-updated: 2026-03-25
tags: [SOPs, workflows, operations, content-machine, whale-hunt, restaurant-collab, newsletter, landing-page]
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

The E-Commerce Customer Audit Workflow for identifying and converting the Top 20% VIP customers.

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

**Current baseline:** ~600–689 Shopify records. ~313–315 paying customers. ~60–62 identified Top 20% Whales.

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

**Meta Ads Whale Targeting:**
- Exclude zip codes too far unless targeting tourists
- Use "Define Further" intersection feature
- Base audience must match competitors like "sushi fine dining" ([[Masa]]) AND match "first business class travel" OR "luxury resorts"

**Background:** This SOP was crystallized after [[Jakub Cambor]]'s agency reported the "EA1" paid post as best-performing (88 ad saves in Ads Manager), while Carl's direct Instagram observation showed the organic "Sabbes" post had 3,500 likes vs. EA1's 422 — with far more meaningful engagement (saves vs. passive likes).

---

## 4. Restaurant Collaboration SOP (Tier System)

Three-tier system for allocating digital support to restaurant partners.

| Tier | Type | What HEAVENSAKE Provides |
|------|------|--------------------------|
| **Tier 1** | Flagship Fine Dining | Custom co-branded graphics, digital menus (to post on brand stories), paid social targeting local audiences, copywriting advice, motion stories |
| **Tier 2** | Established Accounts | Standard co-branded graphics, story reposts, basic guidance, copywriting advice |
| **Tier 3** | Emerging / New Accounts | Reposts on HEAVENSAKE stories ONLY. No dedicated content creation. No digital menus. |

**The principle:** The brand's digital resources are finite. The most culturally impactful partners get the most support. Tier assignment is determined by Carl.

---

## 5. Newsletter Template Rules

**Format mandate:**
- **80% Text / 20% Visual** (one high-quality photo maximum)
- HTML-heavy, image-embedded buttons are **BANNED** — they require constant developer intervention and look too commercial
- Text must be editable HTML (not baked into a JPEG)

**Content philosophy:**
- Must deliver actual value to the customer, not "masturbation" (Carl's word for newsletters that celebrate the brand's own events with no customer value)
- Newsletter subject lines: "Reviving an Icon" approved framing
- No discounts — deliver exclusive access, knowledge, or scarcity instead

---

## 6. Landing Page Architecture

Two types of landing pages, each with distinct UX logic:

**Type A — Events & Experiences (High-Friction)**
- Designed to **gatekeep** information
- Example: Hide the menu or DJ lineup until email is captured
- Goal: Lead generation
- Used for: Monaco F1 party, "A Better High" events, members-only drops

**Type B — Product / Scarcity Drops (Low-Friction)**
- Designed purely for **conversion**
- Must allow customers to discover the full collection without dead-ends
- Text must be editable HTML (not baked into a JPEG)
- Goal: Direct purchase / waitlist completion
- Used for: Sakura Prestige lottery, Hanami drop, Club Heaven membership

---

## 7. Prompt Templates — Brand Voice Guide

Official AI prompt templates for generating compliant HEAVENSAKE content:

| Content Type | Rules |
|-------------|-------|
| **IG Captions** | Maximum **40 words**. Must use 1 sensory hook + 1 heritage phrase. |
| **Editorial** | **300–500 words** bridging Japanese origins with French Assemblage. |
| **Tasting Notes** | Structured strictly as **Nose → Palate → Finish**. Nothing else. |
| **Event Invites** | Must use one phrase from "Collaboration" and one from "Luxury," creating scarcity. |

**Approved Seed Phrases (mandatory hooks):**
- "Silk on the tongue"
- "A garden in bloom on the nose"
- "Moonlight in liquid form"
- "Eternity in a drop" (15-year mountain water filtration)
- "The Third Color"
- "Pure by nature, elevated by art"

---

## 8. Communication Protocol — Brewery Partners

| Scenario | Contact |
|----------|---------|
| Routine operational matters | [[Nana]] (front-facing) |
| Pricing / commercial / strategic | [[Sebastien L'Hermitte]] (escalation) |
| Relationship-critical or crisis | [[Carl Hirschmann]] (personally) |
| Sample logistics / US market | [[Zak Gross]] |

**Cultural note:** Japanese business relationships require consistency, face-saving, and clear communication. When something goes wrong, the fix must be private, fast, and never cause public embarrassment. Standard communications for [[Shichiken]] ([[Nana]]) take ~3 back-and-forth emails; for HEAVENSAKE it currently takes 10 — a known inefficiency being addressed.

---

## 9. Shopify / Tech Stack Access Protocol

| System | Owner | Access Notes |
|--------|-------|-------------|
| [[Shopify]] (US) | [[SIPC]] / [[CIPC]] (distributor) | Admin via "Kevin's account"; requires live 2-step verification code sent to Kevin's email |
| [[HubSpot]] | Internal | PR contacts + basic VIP network; not yet fully linked to Shopify |
| [[Google Analytics 4]] + [[GTM]] | Lauran (former agency) | Active on site; pixel migration in progress |
| [[Meta Business Suite]] | External agency (Lauran's) | Ad account + pixel being migrated back to HEAVENSAKE ownership |
| [[Notion]] | [[Abdel Giant Nerd]] + [[Giancarlo Cappelletti]] | Central operating system; stores processes, supply chain, feeds future AI agent |

---

## Related Notes

- [[Carl's AI Thesis]]
- [[Contradictions & Open Questions]]
- [[Vendors & Agency Failures]]
- [[Team Structure & Roles]]
- [[Master KPIs & Metrics]]
- [[Legal & Compliance]]
