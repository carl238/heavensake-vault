---
type: strategy
source: uploaded-document
status: validated
last-updated: 2026-03-24
tags: [AI, automation, strategy, hubspot, klaviyo, make, notion, abdel, perplexity, B2B, B2C, B2A, GEO]
---

# HEAVENSAKE AI & Automation Strategy

*Source: heavensake-ai-strategy-2.docx — Prepared for Carl Hirschmann, Founder, CEO, Creative Director & CMO | March 20, 2026*
*CONFIDENTIAL*

---

## 1. Executive Summary

Heavensake now operates with Perplexity Computer connected to seven core business systems: Notion, HubSpot, Slack, Google Drive, Klaviyo, Google Analytics, and Shopify. Over the past six months, Abdel has built a comprehensive Notion knowledge base and a suite of Make.com automations that form the operational backbone of the company's logistics, CRM, and data infrastructure.

**Central Question:** What should Perplexity Computer handle directly, what needs Abdel, and what is the optimal division of labor?

**Bottom Line:**
> Perplexity Computer is already a powerful execution layer for B2B outreach, marketing analytics, content creation, and data analysis. Abdel's irreplaceable value lies in infrastructure architecture, Make.com automation design, and complex multi-system workflow engineering.

**Recommended Operating Model:** Abdel as architect + Perplexity Computer as daily operator.

---

## 2. Current State Assessment

### 2.1 Notion — What Abdel Built

Two teamspaces form the operational and marketing backbone:

**HeavenSake IT Infrastructure (16+ pages, well-populated)**
The operational brain of the company. Covers Automation Wiki, Make.com scenarios, software connections, project management, and a 3-month roadmap.

**HeavenSake Marketing (19 pages, partially populated)**
Covers Brand Guidelines Library (17+ items), Sakura Prestige launch trackers (US & JP), Brand & Strategy Hub, and content databases.

**Key Databases:**
- CRM — dynamic and automated via Make.com
- Products/SKUs — comprehensive catalog
- Suppliers — brewery relationships
- Inventory — real-time tracking
- Purchase Orders — automated sync
- Sales Orders — deal tracking
- Invoices — Xero integration

**Gap Identified by Abdel:**
> "We're halfway there. Notion covers existing automations, software connections, Make scenarios, and starting to cover marketing. But company knowledge and brand knowledge are still lacking." — The Sales Order Tracking project is on the backburner, meant to follow an order from client request through to delivery.

### 2.2 HubSpot — Current State from API Audit

A comprehensive API audit reveals both significant assets and critical gaps:

**Pipeline Structure:**
- Sales Pipeline (B2B): 1,037 deals — 1,033 closed won, only 4 open. Active pipeline.
- Shopify Pipeline (B2C): 184 historical records, archived. Dead since 2021.

**Notable Custom Properties:**
- `license_` fields (liquor licenses) — valuable for B2B targeting
- `buying_group` — account segmentation
- `first_time_sake_drinker` — consumer profiling
- `cases` on deals — volume tracking

### 2.3 Slack — Operational Notifications Hub

Slack is used primarily for operational and logistics notifications via Make.com automation, not strategic discussion.
- `#automation-notifications-hs`: Make bot posts shipment status changes and ETA updates for inbound sake shipments from Japanese breweries.
- Error Notifications: Routed to Abdel — 4 Make.com scenario errors logged in February 2026 for Airtable inventory update.
- Strategic Discussions: Happen elsewhere (calls, email, Notion).

### 2.4 Make.com Automations — Abdel's Domain

Abdel manages a suite of production automations that form the data backbone:
- Underlying Databases: Multiple Airtable databases power these automations — Operations (`app5cYjK919CA4hUR`) and Production & Inventory (`app4m0Bf0UmYIVN35`).

---

## 3. The Division of Labor: Perplexity Computer vs. Abdel

**Guiding principle:** Perplexity Computer operates the intelligence and execution layer; Abdel architects the infrastructure and automation plumbing.

| Function | Perplexity Computer | Abdel |
|---|---|---|
| B2B outreach | Profile accounts, write personalized emails, track responses | Sales Order Tracking automation |
| Marketing analytics | Analyze campaign data, iterate creative | Automated follow-up sequences |
| Content creation | Generate copy, social posts, email flows | — |
| Data analysis | HubSpot audits, Klaviyo segmentation analysis | Database architecture |
| Make.com | Review/document existing scenarios (read-only) | Build and modify all automations |
| Webhook/API setup | Document and suggest | Configure and deploy |

---

## 4. The B2B Strategy

### 4.1 Current Assets
- HubSpot: 14,548 companies with custom properties for liquor licenses and buying groups
- PC Capability: Already profiled 100 accounts, found 300+ real contact details with personalized emails
- Zak Gross Classified: 88 TOP tier accounts ready for outreach
- Shopify: Active store for direct sales

### 4.2 Immediate Actions — PC-Led, No Abdel Needed
- Clean HubSpot B2B pipeline — fix lifecycle stages, reassign orphaned accounts, populate company owners
- Profile top 100 US restaurant/bar targets using existing HubSpot data + web enrichment
- Generate personalized cold emails for 20–50 accounts per week
- Monitor ad campaigns (Label Noir already running)
- Track responses, book appointments for Zak

### 4.3 Medium-Term — Abdel Projects
- Sales Order Tracking automation — Abdel's proposed next major project
- Automated follow-up sequences when response volume exceeds manual capacity
- PO-to-invoice chain automation (the trigger chain Abdel described)

---

## 5. The B2C Strategy

### 5.1 Current Assets
- 10,051 marketable contacts in HubSpot
- Shopify store (heavensake.com) — active
- Klaviyo connected for email marketing
- Monaco F1 event June 6 — major content opportunity
- 1,482 Facebook leads from Sakura Prestige campaign (0 converted — needs nurturing)

### 5.2 Immediate Actions — PC-Led
- Build 3-email welcome sequence for new leads (drafted by PC, reviewed by Carl/Claire)
- Segment existing 10K marketable contacts by engagement level
- Run Monaco Grand Prix competition for US cold audience (already strategized)
- Create content calendar for Q2–Q3
- Analyze Label Noir campaign results and iterate

### 5.3 Medium-Term — Abdel Projects
- Reconnect Shopify-HubSpot integration for B2C deal tracking
- Build automated nurturing workflows (abandoned cart, post-purchase, reactivation)
- AI agent team for handling inbound email at scale (Abdel's stated capability)

---

## 6. The B2A (Business-to-Agent) Strategy

This is the frontier Carl identified. As AI agents increasingly mediate consumer decisions, Heavensake needs to be "agent-discoverable."

### 6.1 What This Means
- When someone asks an AI "recommend a premium sake for a dinner party," Heavensake should appear
- GEO audit showed only **33% visibility** on buyer persona queries
- The brand's unique positioning (Franco-Japanese assemblage, Régis Camus cellar master, luxury lifestyle) is citation-worthy but under-indexed

### 6.2 Actions — Mostly PC-Led
- **Ongoing GEO monitoring** — recurring task checking AI visibility weekly
- **Build citation-worthy content:** tasting guides, food pairing data, origin stories, expert interviews
- **Structured data implementation** on website (needs Giancarlo/dev for schema markup)
- **Wikipedia article** (Carl mentioned this) — PC can draft, human submits
- **Backlink strategy** through publications (Carl mentioned respectable source purchases)
- **Ensure Notion brand knowledge** is so rich that any connected AI can represent the brand accurately

---

## 7. The Make.com Question

Carl offered to give Perplexity Computer browser access to Make.com.

### 7.1 What PC Could Do via Browser
- Review existing scenarios and document them
- Identify errors and suggest fixes
- Analyze workflow logic
- Suggest optimizations

### 7.2 What PC Cannot Do
- Reliably build or modify complex Make.com scenarios (too many moving parts, nested conditions, API configurations)
- Debug webhook issues that require testing live data flows
- Set up new integrations with external APIs
- Manage the Airtable database architecture that underlies the automations

### 7.3 Recommendation
Give PC read-only browser access to Make.com for audit and documentation purposes. All modifications should go through Abdel.
> "I wouldn't trust AI to set up an entire automation, especially not something this big." — Abdel

---

## 8. Recommended Engagement Model with Abdel

Based on the call, Carl wants to move from fixed retainer to **project-based billing.**

Key projects to scope:
- Sales Order Tracking system
- Shopify-HubSpot B2C reconnection
- Automated email follow-up sequences
- AI agent team for inbound handling

---

## 9. The 6–12 Month Window of Opportunity

The document emphasizes that this is a critical operational window:
- The AI and automation infrastructure is now in place
- Brand knowledge is being built out in Notion (this vault being a key component)
- The combination of Perplexity Computer (daily operator) + Abdel (architect) + Carl (vision) creates a powerful execution engine

**Key priorities for the window:**
1. Complete the brand knowledge base so AI has full context to represent HEAVENSAKE correctly
2. Build the B2A (GEO) strategy to capture AI-mediated consumer decisions
3. Activate the B2B pipeline with personalized outreach at scale
4. Nurture the 1,482 Facebook leads from Sakura Prestige before they go cold

---

## Related Notes

- [[Meta Ads Knowledge Base]] — current ad strategy
- [[Markets & Strategy]] — broader market strategy
- [[HS 2026 Guidelines Overview]] — 2026 priorities
- [[Buyer Personas]] — consumer segments
