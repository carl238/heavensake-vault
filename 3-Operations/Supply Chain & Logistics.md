---
type: knowledge
status: validated
source: Google Drive (Michele Fincato Email Audit, Executive Meeting Notes, Operations Effectiveness Phase 2, SATOKO Logistics Analysis, Brand KB)
tags: [operations, logistics, supply-chain, shipping, distribution, warehousing]
last-updated: 2026-03-25
---

# Supply Chain & Logistics

A comprehensive map of HEAVENSAKE's global supply chain — from Japanese breweries to end consumers across 14+ markets. [[Michele Fincato]] is the central coordinator for all physical logistics.

---

## Geographic Markets & Distribution Partners

| Market | Distributor / Partner | Status | Notes |
|--------|----------------------|--------|-------|
| **USA** | Park Street (platform), CIPSE/Tipsy (license holder) | Active | HEAVENSAKE cannot sell directly — operates through licensed partner. Any major changes require written confirmation from CIPSE (contact: Alla). |
| **Japan** | Imadeya (retail), UPAC/Japan Post (last-mile) | Active | E-commerce launch May/June 2026. Alcohol license obtained. |
| **Netherlands / EU** | LIS Logistics Amsterdam (warehouse) | Active | €15.50/pallet/week (rented) or ~€15,000 container purchase |
| **UK** | JFC (logistics/distribution), Endo (distributor) | Transitioning | A/B/C distribution options evaluated (Mar 2025) |
| **China** | Telford | Finalized | Terms finalized Feb 2025 |
| **Hong Kong** | GW Cellars + Telford; Pierre | Moving forward | — |
| **Canada** | Benoit (contact) | Active | — |
| **Taiwan** | — | Agreement executed | — |
| **Thailand** | Sake Merchant | Proceed | — |
| **Singapore** | — | Repricing | Warehousing dispute resolved ($5,700) |
| **Turkey** | ADCO | Agreement executed | — |
| **Dubai** | Bar des Pres | Negotiation | $5K launch, $15K annual max |
| **India** | Harsh / Roheen | Gone silent | — |
| **Italy** | Target venues identified | Prospecting | 11 venues listed including Zuma Rome |

---

## Brewery Partners (Japan)

All sake originates from Japanese brewery partners. Orders coordinated by [[Nana|Nana Zomen]], logistics managed by [[Michele Fincato]].

| Brewery | Products | Key Notes |
|---------|----------|-----------|
| **Shichiken** | Label Azur, entry-level | $1M Japan online sales benchmark. Daruma 10-year anniversary ceremony location. 20% price increase expected (rice costs doubled: 100M→200M yen). |
| **Dewazakura** | Label Azur / Noir | Active supplier. PO-00415 tracked (ocean FCL). |
| **Niizawa** | Label Noir, Prestige II | US masterclass planned. Bottle quality crisis — only 24/100 usable (Mar 2025). 24% price increase demand. |
| **Urakasumi** | Label Orange | Active supplier. 3,000 boxes in stock. |
| **Tatenokawa** | Label Noir | Active. |
| **Katsuyama** | — | Active. |
| **Konishi** | Junmai 12 | Active. |
| **Noguchi** | Prestige I | Key bottling partner. Visiting US Sept 2026. |
| **Arita Porcelain Lab** (Matsumoto-san) | Prestige porcelain bottles | Arita region, Saga Prefecture. Hand-dipped pink glaze, kiln-fired. Prestige III (Sakura) pink matte sanded porcelain. |

---

## Shipping Routes & Costs

Based on SATOKO Logistics analysis:

| Route | Total Cost | Per Bottle | Method |
|-------|-----------|------------|--------|
| Japan → California (Ocean) | $9,259 | $1.88 | Ocean FCL |
| Tokyo → New York (Air) | $48,878 | $9.91 | Air freight |
| Tokyo → San Francisco (Air) | $31,183 | $9.48 | Air freight |

### Shipping Conditions
- All sake shipped in **reefer containers at 5°C**
- Three order types:
  1. **B2B / Wholesale** — Ocean FCL from Japan
  2. **B2C / DTC** — `[HS-SHIP] PLEASE PACK – [Country] – [Customer Name] – [AU-Number]`
  3. **Event orders** — One-off logistics for specific events

---

## Freight & Logistics Partners

[[Michele Fincato]] manages all of these relationships:

| Partner | Role | Key Contacts |
|---------|------|-------------|
| **Savino Del Bene** | Primary freight forwarder (Japan-origin) | Kazue Sato, Naoya Saisho, Hiroshi Ikeda, Flavio Gori |
| **Hillebrand Gori** | Wine/spirits logistics | Paola Ballesteros, Melanie Schwalbach, Ulrike Klawunn |
| **Albatrans** | European freight | D. Torres, J. Arrizurieta, M. Wohlers |
| **DSV** | Sea freight Switzerland | Thomas Krause |
| **DB Schenker** | Ocean freight Zurich | — |
| **DHL** | Express / cross-trade | — |
| **XPO Logistics** | European logistics | Massinissa Mansouri |
| **Score Japan** | Japanese logistics / forwarding | — |
| **Tatsumi Custom Services** | Japan customs clearance | A. Semenova, Y. Shibata |
| **Park Street** | US importer / distributor | KDouredjian, freight@parkstreet.com |
| **UPAC (Japan Post)** | Japan DTC last-mile | — |
| **LIS Logistics** | Netherlands/EU warehouse | — |

---

## Warehousing

| Location | Partner | Cost | Notes |
|----------|---------|------|-------|
| Netherlands / EU | LIS Logistics Amsterdam | €15.50/pallet/week (rented) | Cold storage. See [[LIS Logistics Portal]] for full API docs |
| USA | Park Street | Included in distribution | See [[US Inventory — Park Street]] for API-based tracking |
| Japan | — | — | To be determined for e-commerce launch |

### EU Inventory Status (as of March 2026)

Full details: [[EU Inventory Management]]

| Status | Total Bottles | Key Products |
|--------|--------------|---------------|
| **Cleared** (duty-paid, ready to sell) | 915 | J Ginjo Dewazakura (467), Junmai 12 (293), J DaiGinjo Orange (60) |
| **Bonded** (under bond, pending clearance) | 2,400 | J DaiGinjo Orange (925), Sake Baby (501), J DaiGinjo Noir Niizawa (480) |

Automated daily monitoring via Perplexity Computer cron (alerts when cleared stock drops below 50 bottles).

### LIS Logistics API (Reverse-Engineered)

The Vanboxtel portal has been reverse-engineered. Key discovery: the API supports **write operations** (creating sales orders, bulk imports) — not just reading data. This means EU order fulfillment can be automated programmatically.

Full documentation: [[LIS Logistics Portal]]

---

## DTC Fulfillment Workflow

```
Michele sends packing request
→ [HS-SHIP] PLEASE PACK – [Country] – [Customer Name] – [AU-Number]
→ Warehouse (Lucky Sake / LSK) executes and confirms
→ Billing details requested separately for shipping cost recharge
```

---

## Operational Naming Conventions

| Code | Meaning |
|------|---------|
| `[HS-SHIP]` | Internal shipment email prefix |
| `[HS-SHIP][LSK###]` | Inbound shipment from brewery |
| `PO-00###` | Purchase order number |
| `AU-00###` | Airtable order/fulfillment number |
| `LSK###` | Lucky Sake warehouse shipment reference |
| `QGVA00#####` | Savino Del Bene booking reference |

---

## Operations Effectiveness — Known Issues

From the Phase 2 assessment:

1. **Information flows via email** — not segmented or systematized
2. **Too much volume for one person** — [[Michele Fincato]] handles shipping, finance, inventory, and DTC alone
3. **Redundancies across locations** — duplicate processes
4. **Manual processes throughout** — no automation in logistics coordination
5. **Incomplete transport documentation** — causes reactive fire-fighting

### Target Architecture (Airtable-Centric)

The goal is to move logistics coordination into structured Airtable workflows:

1. **Sales Forecast:** Standard entry form — single source of truth per channel/market/product
2. **Inventory Management:** Pull from Park Street (US) + LIS (NL) into dashboard
3. **Production Planning:** PPO in Airtable → Head of Ops approves → brewery/glass producer receives form → auto-creates POs
4. **Forwarding Coordination:** Airtable highlights upcoming pickups with vessel tracker + ETA per shipment
5. **Shipment Documents:** Folder/repository per PO; invoices@heavensake.com for AI pickup; external partners get read access
6. **Logistics Quotation:** Forwarders enter quotes via Airtable form; Ops selects best quote

---

## UK Theft Incident (2024)

- **What:** 160 cases stolen — £31,747 loss
- **Liable:** Robert Kukla
- **Context:** Discussed at Nov 29, 2024 executive meeting
- **Resolution:** Under investigation; informed distribution strategy changes

---

See also: [[Michele Fincato]], [[Sebastian|Sébastien Lhermitte]], [[Nana|Nana Zomen]], [[Ops & Automations — Make.com]], [[Financial Overview]], [[Heavensake Team Overview]], [[LIS Logistics Portal]], [[EU Inventory Management]], [[US Inventory — Park Street]], [[Forwarder & Shipping Management]], [[Automation Registry]]
