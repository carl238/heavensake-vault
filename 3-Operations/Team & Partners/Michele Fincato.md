---
status: validated
source: Google Drive (Michele Fincato Email Audit — 100,172 events, Operations Effectiveness Phase 2, Executive Meeting Notes, ApprovalMax workflow)
tags: [people, core-team, finance, operations, logistics, controller]
last-updated: 2026-03-25
---

# Michele Fincato

**Full Name:** Michele Fincato
**Role:** Financial Controller / Head of Operations & Logistics
**Email:** michele.fincato@heavensake.com
**Location:** Lombardy, Italy
**Reports to:** [[Carl Hirschmann]] (final approver)
**Company:** Lucky Sake AG

---

## Overview

Michele is the operational backbone of HEAVENSAKE — the person who makes the physical supply chain work and keeps the financial books in order. He manages all inbound shipping from Japanese breweries, coordinates with 15+ freight partners globally, handles DTC fulfillment, manages the accounting in Xero, and is the second-to-last approver in the ApprovalMax chain (before Carl).

His role was profiled through a comprehensive email investigation (100,172 Google Workspace Admin audit events), confirming the breadth of his responsibilities.

---

## Responsibilities

### Shipping & Logistics

Michele manages all physical movement of product:

- **Inbound shipments from Japan:** Coordinates POs from all breweries (e.g., PO-00415 Dewazakura Ocean FCL, PO-00332 Noguchi Air)
- **15+ freight/logistics partners:** See [[#Freight Partners]] below
- **DTC fulfillment:** Sends packing requests using format: `[HS-SHIP] PLEASE PACK – [Country] – [Customer Name] – [AU-Number]`
- **Multi-market shipping:** Singapore, Dubai, California, Netherlands, UK, Japan
- **US distribution:** Coordinates with [[Park Street]] (importer/distributor)
- **Shipping conditions:** Sake shipped in reefer containers at 5°C

#### Three Order Types
1. **B2B / Wholesale:** Ocean FCL shipments from Japan
2. **B2C / DTC:** `[HS-SHIP] PLEASE PACK` → warehouse executes → billing for shipping cost recharge
3. **Event orders:** One-off logistics for specific events

### Finance & Accounting

- **ApprovalMax position:** 2nd to last in chain — Zak → Sara → Shotaro → Noemi → Kevin → **Michele** → **Carl (final)**
- **Xero accounting:** Primary controller for Lucky Sake AG international account
- **Overdue invoices:** Follow-up and urgent payment management
- **Trial balance:** YTD TB review with Lucky Holding AG (Swiss holding)
- **Invoice allocation:** Japanese payments (e.g., Imadeya 5,334,000 JPY)
- **Shipping cost recharge:** Bills customers for shipping costs
- **US depletion data:** Tracks Park Street YTD distributor data
- **Event payments:** Confirms event-related payment processing
- **Expense management:** Reporting and oversight

### Inventory & Stock

- Stock and inventory reporting across all locations
- Disposal requests (e.g., LSK-JGINJOSB-720-D)
- Inventory by location group reports
- Coordinates with LIS Logistics Amsterdam (EU warehouse — €15.50/pallet/week)

---

## Freight Partners

Michele coordinates with 15+ logistics partners globally:

| Partner | Role | Key Contacts |
|---------|------|-------------|
| **Savino Del Bene** | Primary freight forwarder (Japan-origin) | Kazue Sato, Naoya Saisho, Hiroshi Ikeda, Flavio Gori |
| **Hillebrand Gori** | Wine/spirits logistics | Paola Ballesteros, Melanie Schwalbach, Ulrike Klawunn |
| **Albatrans** | European freight | D. Torres, J. Arrizurieta, M. Wohlers |
| **DSV** | Sea freight Switzerland | Thomas Krause |
| **DB Schenker** | Ocean freight Zurich | — |
| **DHL** | Express/cross-trade | — |
| **XPO Logistics** | European logistics | Massinissa Mansouri |
| **Score Japan** | Japanese logistics/forwarding | — |
| **Tatsumi Custom Services** | Japan customs clearance | A. Semenova, Y. Shibata |
| **Park Street** | US importer/distributor | KDouredjian, freight@parkstreet.com |
| **UPAC (Japan Post)** | Japan DTC last-mile | — |
| **LIS Logistics** | Netherlands/EU warehouse | — |

---

## Operational Naming Conventions

Michele uses and manages these standard codes:

| Code | Meaning |
|------|---------|
| `[HS-SHIP]` | Internal shipment email prefix |
| `[HS-SHIP][LSK###]` | Inbound shipment from brewery (LSK = Lucky Sake sequence) |
| `PO-00###` | Purchase order number |
| `AU-00###` | Airtable order/fulfillment number |
| `LSK###` | Lucky Sake warehouse shipment reference |
| `QGVA00#####` | Savino Del Bene booking reference |

---

## DTC Fulfillment Workflow

```
Michele sends packing request
→ [HS-SHIP] PLEASE PACK – [Country] – [Customer Name] – [AU-Number]
→ Warehouse (Lucky Sake / LSK) executes and confirms
→ Billing details requested separately for shipping cost recharge
```

---

## Key Systems

| System | Michele's Role |
|--------|---------------|
| **Xero** | Primary controller (Lucky Sake AG account) |
| **ApprovalMax** | 2nd-to-last approver (before Carl) |
| **Airtable** | Inventory, POs, invoices, stock reports |
| **invoices@heavensake.com** | AI-assisted invoice pickup and storage |
| **Bexio** | Switzerland-specific accounting |

---

## Notes

- Michele's scope is unusually broad for one person — the Operations Effectiveness Phase 2 assessment explicitly flagged that too much daily volume flows through a single person
- Pain points identified: information flows via email (not systematized), redundancies across locations, manual processes, incomplete transport documentation causing reactive fire-fighting
- The target architecture aims to move more of Michele's coordination into Airtable (see [[Ops & Automations — Make.com]])
- Accountant search: Consavo firm identified (Feb 2025) to support Michele's workload

---

See also: [[Carl Hirschmann]], [[Sebastian|Sébastien Lhermitte]], [[Sara Vergani]], [[Financial Overview]], [[Ops & Automations — Make.com]], [[Supply Chain & Logistics]]
