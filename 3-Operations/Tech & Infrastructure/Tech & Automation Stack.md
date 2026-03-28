---
type: knowledge
status: validated
last-synthesized: 2026-03-28
source-meetings:
  - 2026-03-20 AI Strategy & Operations — Carl + Abdel.md
  - 2026-02-23 Operational Dashboard & GEO-SEO Marketing Automation.md
  - 2025-10-13 Operations Database & Automation Infrastructure.md
  - 2025-12-17 LLM Strategy & Automation Retainer Review.md
  - 2025-11-18 eCommerce Tech Stack & Infrastructure Planning.md
  - 2026-03-02 Marketing Alignment — Major Session (171min).md
  - 2026-03-19 Carl-Claire - Meta Ads Optimization & Shopify Integration.md
  - 2026-01-13 on board catchup Giancarlo.md
tags: [tech, automation, Shopify, Notion, Airtable, Make, HubSpot, Klaviyo, Meta, GEO, Perplexity]
---

# Tech & Automation Stack

HEAVENSAKE's technology infrastructure is being rebuilt from the ground up in 2026 — moving from disconnected tools and manual processes to an integrated, AI-driven operational nervous system. Abdel Beldy (Giant Nerd) is the primary architect.

---

## Infrastructure Philosophy

The stack must serve two masters:
1. **Operations:** Track every purchase order, invoice, inventory level, and supplier communication in one place
2. **Brand/Marketing:** Give AI tools enough context about the brand (voice, strategy, product knowledge) to operate autonomously on content and outreach tasks

> "You need our information to be complete and we need to have a system that works and that doesn't leave anything outside of the sphere of knowledge."
> — *2026-03-20 AI Strategy & Operations — Carl + Abdel*

The gap that limits AI autonomy today: the operations layer (Notion/database) is largely built, but the **brand knowledge layer** is incomplete. AI cannot generate on-brand content or strategic decisions without the brand's DNA encoded as accessible data.

---

## Core Tools

### Notion — Operational Backbone

**Role:** Knowledge hub, operations database, task management, process documentation

**What's built (as of March 2026):**
- Dashboard live with: purchase orders, sales orders, invoices, inventory
- All primary entities dynamic and automated: POs, invoices, SKUs, products, suppliers (~20 tables)
- Team in active use: Nana, Michele, Sebastien, Gloria using daily
- Replacing unreliable legacy Airtable data

**What's missing:**
- Brand knowledge layer: voice, strategy, product positioning, DNA — not yet in Notion
- This is the primary bottleneck for AI-autonomous brand operations

**Next projects:**
- Sales order tracking (follow order from placement to delivery, all intermediate stages connected)
- Automated reorder triggers (when inventory hits threshold → auto-generate PO to supplier, accounting for lead times and shipping delays)
- Brand/company knowledge population (Giancarlo + Gloria assigned; urgent post-Giancarlo exit)

---

### Shopify — E-Commerce Platform

**Role:** US DTC sales; Japan e-commerce (via Hikari logistics partner)

**Current status:**
- US store live (heavensake-us.myshopify.com)
- Theme: Dawn v15.4.0 ("20260319_giancarlo_def"), ID 128229310513
- Japan store (jp.heavensake.com) in setup — launching with Hanami bottle
- Label Noir/Azur historically ~70% of DTC mix

**Custom API app ("SEO Cleanup Tool"):**
- Created March 28, 2026 for Perplexity Computer theme/file operations
- Client ID: 691f13d87d18ee15ce035425499421ee
- Scopes: write_files, write_script_tags, write_themes
- Note: The Pipedream Shopify connector returns null for all queries — use this custom app or browser instead

**SEO technical fixes deployed (March 28, 2026):**
- Hero image converted to WebP (2.84 MB → 57 KB)
- og:image HTTPS fix, H1 structure fix, heading hierarchy fix
- Product/Organization/Article JSON-LD via GTM (18 pages covered)
- Blog meta descriptions, alt text (products + blog), /collections/sake populated
- Age verification script blocker (MutationObserver workaround for orphaned ScriptTags)
- Full details: [[SEO Technical Status]]

**Active technical issues (March 2026):**
- Meta Conversion API not properly installed — needs developer fix
- Orphaned ScriptTags from uninstalled age verification apps (requires Shopify Support to purge)
- Data sharing set to maximum for Conversions API (Claire confirmed)

**Planned integrations:**
- Perplexity Computer: API access for real-time inventory, customer data, order tracking
- HubSpot CRM: Connected for customer data synchronization
- Klaviyo: Email marketing connected to Shopify purchase events

---

### Make.com — Automation Platform

**Role:** Workflow automation connecting all tools

**Status:** Active; Abdel is primary builder. Audit pending (Carl asked Claire to share access for full audit).

**Active automations being built:**
- Brewery ordering workflow (brewery forms prototype — Abdel)
- Customer segmentation triggers (RFM → inner circle tiers)
- Content automation pipeline (keyword → AI options → review queue)

---

### HubSpot CRM

**Role:** CRM for B2B contacts (restaurant accounts, distributors), PR contact management, RSVP/party funnel

**Active issues:**
- Two-factor authentication updated (March 2026)
- PR contact owner field: new mandatory field — all reps must update existing entries to avoid press inquiries going to press@evansake.com
- Password reset/access issues being resolved (Carl + Claire coordinating)

**Integration with Perplexity:** HubSpot + Meta Ads Manager integration with AI tools is a near-term priority (Carl, March 2026).

---

### Klaviyo — Email Marketing

**Role:** Newsletter, DTC email sequences, membership communication

**Migrated from HubSpot** (January 2026). Why: better e-commerce integration, more powerful segmentation, better UX for the team.

**Active issues:**
- Mobile display: newsletter mobile display has UX problems — must be fixed urgently before any growth campaign
- Welcome sequence: needs complete rewrite (leads with Assemblage, should lead with brand mission)
- Access: Claire obtaining full access post-Giancarlo

**Planned sequences:**
- Welcome/onboarding (rewrite urgently)
- VIP inner circle care sequences (Top 5 / Top 50 / Top 200)
- Post-purchase (thank you + brand story)
- Prestige 3 launch (to existing Prestige customers)
- Membership welcome + onboarding

---

### Meta Ads Manager

**Role:** Paid social advertising (US and Japan markets)

**Active issues:**
- Pixel installation: incomplete — needs developer fix
- Ad account: verification required to enable retargeting (identified March 2026)
- Current $10,000 in identified spend; domain verification blocking some campaigns
- Paused/rejected ads due to pixel and verification issues

**Strategy:**
- Increase budget to hit 50+ optimization events/week (current 1,000€/month = ~25/week)
- Focus on Add-to-Cart events before Purchases (build optimization signal)
- Integrate AI for campaign analysis and creative testing
- Perplexity vs. Manus head-to-head comparison test planned

**Paid ads start date:** April 5, 2026 (post-Giancarlo transition)

---

### Google Analytics / Reporting

**Role:** Web traffic, e-commerce performance, campaign attribution

**Issue:** Analytics not properly integrated with Meta for cross-channel attribution — making ROI assessment imprecise.

---

### Perplexity Computer — AI Primary Tool

**Role:** Prospect research, outreach personalization, website fixes, campaign analysis, content calendar generation

**Status:** APPROVED as the central AI tool for B2B/B2C/B2A (March 2026). Carl personally tested and uses actively.

**Live capabilities deployed:**
- Restaurant prospect research: existing account list → finds similar venues → 3 contact persons per venue → LinkedIn + email
- Personalized outreach at scale: reads each contact's LinkedIn, Instagram, recent press → customizes email intro
- 90-day LinkedIn content calendar generation
- Website technical fixes (Carl used it to repair Japanese programmer errors)
- Shopify API integration (in progress)

**Operations automation (March 2026 — live):**
- Monthly Sales Report: Park Street API + Xero → Google Sheets (1st of each month)
- Japan Order Monitor: Email scanning for new order requests (3x daily)
- EU Stock Report: LIS portal download → classify → alert on low stock (daily)
- Auto-Invoice: Airtable shipped POs → Xero invoice creation (2x daily)
- Park Street API integration (4 endpoints, token-based auth)
- LIS Logistics API reverse-engineering (full write access discovered)
- Xero API: Full CRUD for invoices, quotes, POs, contacts

**Data quality & monitoring automation (March 28, 2026 — live):**
- Weekly Data Quality Check: Scans 6 Airtable tables for issues (Mondays 9am CET)
- Monthly Operations Digest: Pre-Abdel meeting summary (12th of month)
- Brewery Form Response Check: Cross-references submissions vs 6 expected breweries (3rd of month)
- Notion KB Freshness Review: Checks for stale pages and gaps (1st of month)
- Invoice & SKU Validation: Linkage % and orphan detection (5th of month)
- All monitoring tasks deliver via email — read-only, never modify data

**Impact:** 82% reduction in Michele's operational workload (~41 hrs/month → ~7.25 hrs/month). See [[Automation Registry]] and [[SOP Analysis — Complete Index]]. See [[Airtable Data Quality]] for current data quality status.

**Connected APIs (via Perplexity Computer):**

| System | Connection | Key Detail |
|---|---|---|
| Park Street | REST API, token auth | 4 tested endpoints, $11.4M historical data |
| Xero | OAuth connector | Tenant: Lucky Sake AG (8f11ebc0-...) |
| Google Sheets | OAuth connector | Sales Report spreadsheet (134V8ne...) |
| Airtable | OAuth connector | Operations base (app5cYjK919CA4hUR, 30 tables) |
| LIS Logistics | Reverse-engineered API | Same-origin only; write access available |
| Gmail | OAuth connector | Email scanning for Japan orders |
| Slack | Direct connector | Notifications |

**Team training:** Carl to organize periodic Perplexity training sessions for Claire and the team.

---

### GEO Stack (Generative Engine Optimization)

**Role:** Optimize HEAVENSAKE's presence in AI-generated search responses (LLMs, not Google)

**Led by:** Abdel's GEO team

**Budget:** €2,900/month (3-month trial approved December 2025)

**Tracking:** Mention percentage across 6 major LLMs (GPT-4, Claude, Gemini, Perplexity, Mistral, Grok)

**Results:** Went from low single-digit to low double-digit mention percentage in 2 months

**Next priorities:**
- Wikipedia article creation for HEAVENSAKE (LLM authority signal)
- External outreach for brand mentions in authoritative sources
- Technical schema updates and website optimization

---

### Airtable — Legacy

**Role:** Previously used for operations database

**Status:** Being replaced by Notion. Legacy data migrated. No longer primary tool.

---

### Dropbox — Asset Management

**Role:** Video, photography, creative asset storage and backup

**Issue:** Raw video and creative assets need to be organized systematically (Claire assigned March 2026). Backup system needed.

---

## Integration Map

```
Notion (Operations) ←→ Make.com (Automation)
Shopify (E-commerce) ←→ Klaviyo (Email)
Shopify ←→ HubSpot (CRM)
Shopify ←→ Meta Ads Manager (Conversions API)
Meta Ads Manager ←→ Google Analytics
Perplexity Computer ←→ LinkedIn (content scheduling)
Perplexity Computer ←→ Shopify (via custom API)
Perplexity Computer ←→ HubSpot (outreach and CRM)
Notion ←→ Copywriting AI Agent (in testing via Abdel)
```

---

## What's Broken / Outstanding (March 2026 Priority List)

| Issue | Urgency | Owner |
|-------|---------|-------|
| Meta Conversions API installation | **Critical** | Digital team + Carl |
| Klaviyo mobile newsletter display | **Critical** | Claire |
| Domain verification (heavensake.com) | **High** | Carl |
| Shopify API scopes update for Perplexity | **High** | Carl |
| HubSpot 2FA + access | **High** | Carl + Claire |
| Notion brand knowledge layer | **High** | Claire + Gloria + Abdel |
| ~~Shopify orphan collections cleanup~~ | **Done** | Perplexity Computer (March 28) |
| Orphaned ScriptTags (age verification) | **Medium** | Shopify Support (only they can purge) |
| Make.com automation audit | **Medium** | Claire (share access) |
| Dropbox asset organization + backup | **Medium** | Claire |
| NFC tag implementation (brewery) | **Medium** | Nana + Sebastien |

