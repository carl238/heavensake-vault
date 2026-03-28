---
title: HEAVENSAKE Ops & Automations
tags: [heavensake, operations, make-com, automation, park-street, xero, airtable, inventory, invoices]
created: 2026-03-25
related:
  - "[[HEAVENSAKE Brand Knowledge Base]]"
  - "[[HEAVENSAKE Vault Index]]"
---

# HEAVENSAKE Ops & Automations

This document maps the entire Make.com automation infrastructure powering HEAVENSAKE's operations. It covers every active scenario, connection, data flow, credit budget, incident history, and optimization opportunity. Use it as the single source of truth for how the backend runs.

> **Make.com account:** HEAVENSAKE OPS (eu2.make.com)
> **Plan:** Pro — $62.35/month, 40,000 credits/month
> **Billing cycle:** 14th to 14th of each month
> **Team:** Carl (Admin), Sara (Owner), [[Abdel]] (App Developer/Automation Specialist), automation@heavensake.com (Admin service account)

---

## Table of Contents

- [[#System Architecture Overview]]
- [[#Scenarios — Active]]
- [[#Scenarios — Inactive / Archive]]
- [[#Nightly Batch Orchestration]]
- [[#Dashboard System]]
- [[#JP Brewery Forms System]]
- [[#Connections Inventory]]
- [[#Webhooks Inventory]]
- [[#Data Stores & Structures]]
- [[#Credit Usage & Budget]]
- [[#Incident History]]
- [[#Notification Settings]]
- [[#Connected Systems Map]]
- [[#Optimization Opportunities]]
- [[#Make.com Platform Knowledge]]

---

## System Architecture Overview

HEAVENSAKE's Make.com instance serves as the **operational nervous system** connecting:

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│  Park Street │────▶│              │────▶│  Airtable   │
│  (US Distro) │     │              │     │  (Ops DB)   │
└─────────────┘     │              │     └─────────────┘
                     │   Make.com   │
┌─────────────┐     │  (HEAVENSAKE │     ┌─────────────┐
│    Xero      │────▶│    OPS)     │────▶│   Slack     │
│ (Accounting) │     │              │     │ (Alerts)    │
└─────────────┘     │              │     └─────────────┘
                     │              │
┌─────────────┐     │              │     ┌─────────────┐
│  JotForm /   │────▶│              │────▶│   Notion    │
│  Cognito     │     │              │     │  (Docs)     │
└─────────────┘     └──────────────┘     └─────────────┘
```

### Core Data Flows

1. **Inventory Pipeline** — Park Street & LIS → Airtable (daily, 22:00 UTC)
2. **Purchase Orders** — Xero → Airtable (daily, 22:10 UTC)
3. **Invoices** — Xero → Airtable (daily, 07:11 UTC)
4. **Quotes** — Xero → Airtable (daily, 22:00 UTC)
5. **Shipment Tracking** — ScraperAPI → Airtable → Slack notifications
6. **Dashboards** — On-demand via webhook when page is accessed
7. **JP Brewery Inventory** — JotForm → Data Store → Airtable

> [!tip] Cross-reference
> For how these systems support the brand strategy, see [[HEAVENSAKE Brand Knowledge Base#Distribution & Sales]] and [[HEAVENSAKE Brand Knowledge Base#Japan Market Strategy]].

---

## Scenarios — Active

### Tier 1: High-Volume / Critical

| Scenario | Folder | Frequency | Ops/Run | 30d Runs | Modules | Notes |
|---|---|---|---|---|---|---|
| **Park Street & LIS Inventory → Airtable** | OPS Datasources | Daily 22:00 UTC | ~828 | 21,705 | 73+ | Biggest credit consumer (~62% of monthly budget). Syncs US inventory data from Park Street distribution platform into Airtable. Was auto-deactivated by Make on 23.02.2026 due to error — manually reactivated by [[Abdel]] same day. |
| **Park Street - Handle New&Updated Shipments** | Sales | Daily 13:00 UTC | 69–148 | 3,796 | 49+ | Processes new and updated shipment records. Variable ops = different data volumes each day. [[Abdel]] actively maintains (edited 23.03.2026). |
| **New POs to both DBs** | OPS Datasources | Daily 22:10 UTC + API-triggered | 1–37 | 719 | 37+ | Syncs new purchase orders from Xero to both databases. Most runs = 1 op (no new POs). 37 ops when POs found. |
| **Xero NEW Invoices to Airtable** | OPS Datasources | Daily 07:11 UTC | 1–12 | 550 | 23+ | Morning invoice sync. High data transfer (80.2 MB/30d) despite low ops — large invoice payloads. |

### Tier 2: Operational

| Scenario | Folder | Frequency | Ops/Run | 30d Runs | Modules | Notes |
|---|---|---|---|---|---|---|
| **Dashboard 1 - inventory** | dashboard page | On-demand (webhook) | 6 | 306 | 2+ | Fires when dashboard page is accessed. 2–6x/day. |
| **Xero Quotes to New DB v1** | OPS Datasources | Daily 22:00 UTC | 12 | 252 | 36+ | Had major failure cascade on 20.02.2026 (see [[#Incident History]]). |
| **Shipments ETA - Send Notification** | Sales | Scheduled + manual | 12–14 | 240 | 7+ | Uses ScraperAPI for ETA data. Pipeline: Get Shipments → Get ETA → Update → Router → Get PO → Slack notification. 7-min duration for scheduled runs. |
| **Dashboard 4 - INVS** | dashboard page | On-demand (webhook) | 6 | 159 | 2+ | Invoice dashboard. High data transfer (152.1 MB/30d) — large invoice payloads. |
| **Dashboard 2 - POS** | dashboard page | On-demand (webhook) | 6 | ~12 | 2+ | Purchase order dashboard. |
| **Dashboard 3 - SOs** | dashboard page | On-demand (webhook) | 6 | ~18 | 2+ | Sales order dashboard. |

### Tier 3: Supporting

| Scenario | Folder | Frequency | Ops/Run | Notes |
|---|---|---|---|---|
| **JP BREWERY FORMS CHECK SUBMISSIONS** | JP BREWERY | Scheduled | varies | 27 runs/30d. Checks for new brewery form submissions. Part of the [[#JP Brewery Forms System]]. |
| **JP BREWERY FORMS RECEIVE SUBMISSIONS** | JP BREWERY | Webhook (instant) | varies | 39 runs/30d. Receives incoming form data via webhook. |
| **JP BREWERY FORMS SEND FORMS** | JP BREWERY | Scheduled | varies | 21 runs/30d. Sends forms to brewery partners ([[Dewazakura]], [[Niizawa]], [[Urakasumi]], [[Konishi]]). |
| **Manual start PO import** | — | On-demand | varies | API-triggered PO import. Last created 17.03.2026. |
| **Product family search and mapping** | — | Daily ~22:05 UTC | ~4 | Discovered in credit logs. Runs as part of nightly batch. |
| **Trigger Inventory Update daily** | — | Daily 22:00 UTC | 1 | Orchestrator that triggers the inventory pipeline. |
| **Cognito - Order Form Submissions** | Sales | Webhook | varies | CognitoForms order processing. |
| **Japan inventory form** | Sales | Webhook | varies | Japan-specific inventory form processing. Related to [[HEAVENSAKE Brand Knowledge Base#Japan Market Strategy]]. |
| **Docubot communications** | — | Webhook | varies | Slack + AI Agent integration. |
| **Priority matrix display page** | — | On-demand (webhook) | varies | Notion-connected priority display. |
| **Sales** | Sales | varies | varies | General sales scenario. |

---

## Scenarios — Inactive / Archive

These can be cleaned up. Classification:

### Safe to Delete (one-time fixes, job done)
- **Fixing missing POs 00283>00287** — one-time data fix
- **PO status fix** — one-time data fix
- **Import old POs to both DBs** — historical migration

### Safe to Delete (superseded)
- **Park Street & LIS Inventory → NEW DB** — replaced by active version

### Safe to Archive or Delete (test/prototypes)
- **Integration Gmail** — test
- **Integration HubSpot CRM** — test
- **Integration JSON** — test
- **Integration Xero** — test
- **Xero watch events webhook** — test
- **Xero Watch purchase orders** — test
- **Xero Watch purchase orders test version** — test
- **Notion documentation bot** — prototype

### Review Before Deleting (event-specific)
- **Event 1 forms** — event-specific, may be needed for future events. See [[HEAVENSAKE Brand Knowledge Base#Events & Experiences]] for event strategy.
- **Event 2 form submissions** — event-specific
- **First Event Email Confirmation** — event automation template

### Empty Folder to Delete
- **Gmail to ChatGPT Drafting Response System** — 0 scenarios, abandoned project

---

## Nightly Batch Orchestration

[[Abdel]] has built a coordinated nightly batch that runs in sequence starting at 22:00 UTC:

```
22:00 UTC ─── Trigger Inventory Update daily (1 op)
    │
    ├──▶ Park Street & LIS Inventory → Airtable (~828 ops, 6-8 min)
    │
22:00 UTC ─── Xero Quotes to New DB v1 (~12 ops)
    │
22:05 UTC ─── Product family search and mapping (~4 ops)
    │
22:10 UTC ─── New POs to both DBs (1-37 ops)
```

### Morning Run
```
07:11 UTC ─── Xero NEW Invoices to Airtable (1-12 ops)
```

### Afternoon Run
```
13:00 UTC ─── Park Street - Handle New&Updated Shipments (69-148 ops)
```

### On-Demand (dashboard access)
```
Any time ──── Dashboard 1-4 (6 ops each, triggered by page view)
```

---

## Dashboard System

All four dashboards use an **on-demand webhook pattern** — they only fire when someone views the dashboard page, saving thousands of operations vs. scheduled polling.

| Dashboard | Data | Webhook | Avg Runs/Day |
|---|---|---|---|
| Dashboard 1 - inventory | Inventory levels | Gateway webhook | 2–6 |
| Dashboard 2 - POS | Purchase orders | Gateway webhook | ~0.4 |
| Dashboard 3 - SOs | Sales orders | Gateway webhook | ~0.6 |
| Dashboard 4 - INVS | Invoices | Gateway webhook | ~5 |

Each dashboard scenario: Gateway (webhook) → Airtable (fetch data) → JSON (format response).

Dashboard 4 has notably high data transfer (152.1 MB/30d) despite low ops — invoice payloads are large.

---

## JP Brewery Forms System

Three-scenario architecture with clean separation of concerns:

```
JP BREWERY FORMS SEND FORMS
    │ (sends forms to brewery partners)
    ▼
JP BREWERY FORMS RECEIVE SUBMISSIONS
    │ (receives completed forms via webhook)
    ▼
JP BREWERY FORMS CHECK SUBMISSIONS
    │ (validates and processes submissions)
    ▼
Data Store: formdates (240 records, 18.8 KB)
    │
    ▼
Airtable (final destination)
```

Used for managing inventory data from Japanese brewery partners ([[Dewazakura]], [[Niizawa]], [[Urakasumi]], [[Konishi]]).

> [!tip] Cross-reference
> For Japan market context and brewery relationships, see [[HEAVENSAKE Brand Knowledge Base#Japan Market Strategy]] and the brewery partner profiles in [[HEAVENSAKE Brand Knowledge Base#Key People & Relationships]].

---

## Connections Inventory

### Active & Intentional

| Connection | Service | Scenarios | Purpose |
|---|---|---|---|
| [[Abdel]] | Airtable (OAuth) | 14 | Primary Airtable access (usrZS6NZgdtr3AsYw) |
| My Airtable Token/Key | Airtable (API Key) | 14 | Token-based Airtable access |
| My Airtable OAuth | Airtable (OAuth) | 4 | Different user (usrMnWgveohTKQmAO) — intentional |
| My Xero connection | Xero | 7 | Primary accounting integration |
| AbdelHeavenSake | Slack (user) | 10 | HEAVENSAKE workspace — user token |
| [[Abdel]] (bot) connection | Slack (bot) | 1 | HEAVENSAKE workspace — bot token (different scopes, intentional) |
| My Slack (user) [giantnerd] | Slack (user) | 3 | Giantnerd workspace — separate org |
| My Gmail connection | Gmail | 2 | automation@heavensake.com |
| My HubSpot CRM connection | HubSpot CRM | 3 | automation@heavensake.com |
| My Others (SMTP) | SMTP | 2 | Email sending |
| My Google connection | Google | 1 | abdel@giantnerd.online |
| My Google Restricted (2) | Google Restricted | 2 | events@heavensake.com — active one |
| My Make (OAuth2) | Make | 1 | Make-to-Make orchestration |
| [[Abdel]] make hs token | GitHub | 4 | Dev integration |
| OpenAI | OpenAI | 3 | AI features |
| Automation HS | JotForm | 1 | JP Brewery forms |
| Notion2 | Notion (MCP) | 1 | Active Notion connection |
| [[Abdel]]'s workspace | Notion | 1 | Separate Notion workspace |
| My Cognito (2) | CognitoForms | 1 | Active forms connection |

### Orphaned — Safe to Remove (0 scenarios)

| Connection | Service | Notes |
|---|---|---|
| My Slack (user) [heavensake] | Slack | Duplicate of AbdelHeavenSake, 0 scenarios |
| My Google Restricted (1) | Google Restricted | events@heavensake.com duplicate, 0 scenarios |
| My Xero (Webhook) | Xero | Lucky Sake AG — unused |
| Giant Nerd | Xero Event | Unused |
| My OpenAI connection | OpenAI | Duplicate of active "OpenAI", 0 scenarios |
| Notion MCP | Notion | Duplicate of active "Notion2", 0 scenarios |
| My Cognito (1) | CognitoForms | Unused, 0 scenarios |

**Total: 7 orphaned connections safe to remove.**

> [!warning] Do Not Merge
> The Slack bot vs. user connections are intentional (different OAuth scopes). The multiple Airtable connections map to different users. The CognitoForms connections were for different user permissions. Always map connections to scenarios before removing.

---

## Webhooks Inventory

26 webhooks total, all showing 0 queued items as of March 2026.

**Key webhooks (active):**
- Dashboard 1–4 endpoints (Gateway webhooks)
- All brewery forms (JP Brewery system)
- Park/LIS inventory to Airtable
- Purchase Order Updated
- Dewazakura Watcher
- Priority-matrix
- Documentation agent call
- Event confirmation Email

**Likely stale (review needed):**
- GN watch events
- Various test/internal webhooks

> [!info] Webhook Expiration
> Make.com deactivates webhooks not connected to an active scenario for 5+ days. They return HTTP 410 Gone. Re-enable by reconnecting and activating.

---

## Data Stores & Structures

### Data Store
| Name | Records | Size | Capacity | Used By |
|---|---|---|---|---|
| formdates | 240 | 18.8 KB | 10 MB | 2 scenarios (JP Brewery forms) |

Storage allowance: 40,000 credits ÷ 1,000 = **40 MB total available**.

### Data Structures (6)
- formdates — JP Brewery form dates
- INVOICES for dashboard — Dashboard 4 response format
- My data structure — General purpose
- notion projects — Notion integration format
- PO for dashboard — Dashboard 2 response format
- SO data for dashboard — Dashboard 3 response format

---

## Credit Usage & Budget

### Monthly Budget: 40,000 credits

#### Estimated Monthly Consumption (based on 30-day data)

| Scenario | Daily Ops (est.) | Monthly (est.) | % of Budget |
|---|---|---|---|
| Park Street & LIS Inventory | ~828 | ~24,840 | 62.1% |
| Park Street Shipments | ~115 | ~3,450 | 8.6% |
| Xero Invoices | ~18 | ~540 | 1.4% |
| Dashboard 1 (inventory) | ~60 | ~1,800 | 4.5% |
| Dashboard 4 (INVS) | ~30 | ~900 | 2.3% |
| Xero Quotes | ~12 | ~360 | 0.9% |
| Shipments ETA | ~35 | ~1,050 | 2.6% |
| New POs to both DBs | ~24 | ~720 | 1.8% |
| JP Brewery (3 scenarios) | ~3 | ~90 | 0.2% |
| All others | ~30 | ~900 | 2.3% |
| **Total estimate** | **~1,155** | **~34,650** | **86.6%** |

> [!warning] Credit Headroom
> Normal operations consume ~87% of budget. Heavy inventory/invoice days push higher. Overages occurred in December 2025 ($3.90) and February 2026 ($5.85). Error cascades (like the Xero Quotes incident) can spike usage further.

#### Overage History
| Period | Amount | Cause |
|---|---|---|
| Feb 2026 | $5.85 (3 charges, Feb 12-13) | Xero Quotes failure cascade with exponential backoff |
| Dec 2025 | $3.90 (1 charge, Dec 11) | Likely similar scenario error loop |

#### Auto-Purchase Credits
- **Current state: OFF**
- When enabled: adds 10,000 credits at $19.50 per purchase, up to 4x/month (max $78/month extra)
- **Path:** Organization Dashboard → Credits auto-purchasing toggle, OR Subscription → Extra credits auto-purchasing
- Payment method on file: Mastercard ••••1759

> [!danger] Risk: Auto-Purchase OFF
> With auto-purchase OFF and regular 90-100% utilization, scenarios will HALT mid-month if credits run out. This means no inventory sync, no invoice processing, no shipment tracking until the next billing cycle. Consider enabling auto-purchase as insurance.

---

## Incident History

### 2026-02-23 — Park Street Inventory Auto-Deactivation
- **What:** Make automatically deactivated the Park Street & LIS Inventory scenario due to a fatal error
- **Impact:** Scenario offline for unknown period on 23.02.2026
- **Resolution:** [[Abdel]] manually reactivated at 10:09:32 same day
- **Status:** Running clean since
- **Lesson:** No automated alerting to Slack — deactivation was detected manually

### 2026-02-20 — Xero Quotes Failure Cascade
- **What:** Xero Quotes to New DB v1 experienced repeated failures triggering Make's exponential backoff
- **Progression:** Paused 1min → 2min → 5min → 10min → 60min → 180min
- **Total downtime:** ~4+ hours
- **Recovery:** Self-recovered on 21.02.2026 at 02:20
- **Impact:** Each retry consumed operations, likely contributing to the $5.85 overage on Feb 12-13
- **Root cause:** Likely Xero API issue (transient)

### 2025-12-11 — Credit Overage
- **What:** $3.90 overage charge
- **Likely cause:** Similar scenario error loop consuming extra credits near end of billing cycle

---

## Notification Settings

**Path:** Left sidebar → Utilities → Notification options

| Setting | Status | What It Does |
|---|---|---|
| Warning in scenario run | ✅ ON | Alerts for warnings needing attention (e.g., data store capacity) |
| Errors in scenario run | ✅ ON | Alerts for errors stopping scenarios |
| Scenario deactivation | ✅ ON | Alerts when scenarios deactivated due to critical issues |

**Delivery:** Email to organization admins only. No Slack integration available in Make.com's native notification system.

**No per-scenario notifications** — organization-wide only.

**No credit threshold alerts available** on any plan. No "alert at 80% usage" feature exists. The only credit-related protection is auto-purchase or scenario deactivation notifications when credits run out.

> [!note] Workaround for Slack Alerts
> To get Slack notifications for errors/deactivations, build a Make scenario that monitors execution logs via the Make API and posts to Slack. This would require using the Make API (available on Pro plan at 240 calls/min).

---

## Connected Systems Map

### Primary Systems

| System | Role | Connection Type | Key Data |
|---|---|---|---|
| **Airtable** | Operations database | OAuth + API Key (3 connections) | Inventory, POs, invoices, quotes, shipments |
| **Xero** | Accounting | OAuth (1 connection) | Invoices, purchase orders, quotes |
| **Slack** | Team notifications | User + Bot tokens (3 connections) | Shipment alerts, error notifications |
| **Park Street** | US distribution | Custom webhook | Inventory levels, shipment data |

### Secondary Systems

| System | Role | Connection Type | Key Data |
|---|---|---|---|
| **JotForm** | Brewery forms | API (1 connection) | JP brewery inventory submissions |
| **CognitoForms** | Order forms | API (1 connection) | Order submissions |
| **HubSpot CRM** | Sales pipeline | OAuth (1 connection) | Contacts, deals |
| **Notion** | Documentation | MCP + OAuth (2 connections) | Priority matrix, project docs |
| **Gmail** | Email | OAuth (1 connection) | Automated emails |
| **SMTP** | Email sending | Credentials (1 connection) | Transactional emails |
| **GitHub** | Code/dev | Token (1 connection) | Automation code |
| **OpenAI** | AI features | API key (1 connection) | Docubot, AI agent |
| **ScraperAPI** | Web data | API key (via HTTP) | Shipment ETA tracking |
| **Make API** | Self-orchestration | OAuth (1 connection) | Scenario triggering |

### Perplexity Computer — Parallel Automation Layer (March 2026)

In addition to Make.com, HEAVENSAKE now has a second automation layer running via Perplexity Computer. These two systems complement each other:

| Task | Platform | Schedule |
|---|---|---|
| Monthly Sales Report (Park Street + Xero → Google Sheets) | Perplexity Computer | 1st of month, 9am CET |
| Japan Order Monitor (email scanning for new orders) | Perplexity Computer | 3x daily, weekdays |
| EU Stock Report (LIS download + classify + alert) | Perplexity Computer | Daily, weekdays 8am |
| Auto-Invoice Shipped POs (Airtable → Xero) | Perplexity Computer | 2x daily, weekdays |
| Nightly inventory/PO/invoice sync | Make.com | Daily 22:00–22:10 UTC |
| Shipment ETA tracking + Slack alerts | Make.com | Daily 13:00 UTC |
| Dashboard data (on-demand) | Make.com | Webhook-triggered |
| JP Brewery forms | Make.com | Scheduled + webhook |

See [[Automation Registry]] for the unified view of all automations across both platforms.

### External Systems NOT Yet Connected (Potential)

| System | Current Use | Automation Potential |
|---|---|---|
| **Klaviyo** | Email marketing | Order confirmations, shipment notifications to customers. See [[HEAVENSAKE Brand Knowledge Base#Digital Strategy & Technology]]. |
| **Shopify** | E-commerce (via Sipsy) | Order sync, inventory updates |
| **Imadeya** | Japan distribution | Japan inventory sync (mirror Park Street pattern). See [[HEAVENSAKE Brand Knowledge Base#Japan Market Strategy]]. |
| **Google Analytics** | Website analytics | Automated reporting |
| **Google Sheets** | Reporting | Dashboard data export |

---

## Optimization Opportunities

### 1. Park Street Scenario Ops Reduction
The Park Street & LIS Inventory scenario at 828 ops/run consumes 62% of the monthly budget. Even a 20% reduction frees ~5,000 ops/month.

**Potential approaches:**
- Audit whether all 73+ modules fire every run or if some paths are rarely taken
- Use filters before database writes to skip unchanged records
- Use aggregators to batch Airtable writes
- Consider breaking into sub-scenarios with conditional triggers

### 2. Auto-Purchase Credits
Enable auto-purchase to prevent scenarios from halting mid-month. Cost is small ($19.50/10K credits) vs. risk of operational blind spots.

### 3. Error Handling Enhancement
Add Break error handlers with max retry limits to Xero-connected scenarios to prevent credit-burning failure cascades. Include Slack notification on error routes.

### 4. Credit Tier Evaluation
At ~87% average utilization with occasional overages, options:
- **Stay on 40K, optimize Park Street** — if reduced to ~600 ops/run, comfortable headroom
- **Upgrade to 80K credits** — more breathing room, lower per-credit cost
- **Pro plan scales to 8M credits** — next tier available without switching plans

### 5. Japan Market Automation
Mirror the Park Street inventory pattern for Imadeya (Japan distributor) when ready. Same architecture: daily sync → Airtable → dashboard. This aligns with the Japan e-commerce launch priority described in [[HEAVENSAKE Brand Knowledge Base#Japan Market Strategy]].

### 6. HubSpot Sales Alerts
Existing HubSpot connection (3 scenarios) could expand to real-time deal notifications → Slack.

### 7. Klaviyo Integration
Existing Klaviyo connector could power customer-facing shipment notifications, triggered by the Shipments ETA scenario.

---

## Make.com Platform Knowledge

### Operations/Credits Model
- 1 module run on 1 bundle = 1 credit
- Triggers always = 1 op regardless of bundles returned
- Routers, filters, error handlers = 0 ops (free)
- Aggregators = 1 op (collapse N bundles to 1)
- N bundles × M downstream modules = N × M ops (multiplier effect)

### Scheduling
- Pro plan minimum: 1-minute intervals
- Max execution time: 40 minutes
- On-demand scheduling = only fires via API or manual trigger

### Error Handling Types
1. **Ignore** — suppress and continue (non-critical lookups)
2. **Break** — store as incomplete execution, continue other bundles
3. **Resume** — provide fallback value, continue
4. **Retry** — retry N times with delay (transient errors)
5. **Rollback** — undo all changes (atomic operations)

### Webhook Limits
- Queue: 667 items per 10K credits (max 10K items)
- Rate: 300 requests per 10 seconds
- Expiration: 5 days without active scenario → auto-deactivated
- Log retention: 3 days (Pro), 30 days (Enterprise)

### Data Store Limits
- Storage: credits ÷ 1,000 = MB available
- 40K plan = 40 MB total
- Max 1,000 data stores per org

### Plan Limits (Pro)
- 40,000 credits/month (scalable to 8M)
- 250 MB max file size
- 30-day execution log retention
- Full-text log search
- Priority scenario execution
- 240 API calls/min
