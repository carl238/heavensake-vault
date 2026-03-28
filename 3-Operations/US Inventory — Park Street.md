---
type: reference
status: active
tags: [inventory, US, park-street, API, automation]
last-updated: 2026-03-28
---

# US Inventory — Park Street

US warehouse inventory management via the Park Street API. Fully automated — no manual exports required.

---

## Overview

Park Street manages US warehousing as part of the HEAVENSAKE distribution relationship. Inventory data is available in real time via the Park Street API, replacing Michele's manual weekly export process.

| Field | Value |
|---|---|
| **Warehouse Operator** | Park Street |
| **Market** | United States |
| **API Base** | `https://api.parkstreet.com/public_apis/` |
| **Auth** | Token: `f25e6217724e35a33a8fc80e723741bfea944553` |
| **Automation Status** | ✅ 100% AUTOMATED |

---

## Key API Endpoints

### Current Inventory Snapshot

```http
POST /get_product_inventory_snapshot
```

Returns per-SKU inventory with full warehouse breakdown:

| Field | Description |
|---|---|
| `on_hand` | Total bottles in warehouse |
| `available` | Bottles available for new orders |
| `allocated` | Bottles reserved for pending orders |

**Data volume:** 87 inventory product-location combinations across 105 product SKUs.

### Historical Inventory Adjustments

```http
POST /inventory_adjustment
```

Returns per-product transaction history. Requires:
- `product` — SKU identifier
- Date range parameters

Useful for auditing stock movements, shrinkage, and reconciliation.

---

## Manual Process Replaced

This automation replaces Michele's **Process 4** (see [[SOP Analysis — Complete Index]]):

| Step | Old Manual Process | New Automated Process |
|---|---|---|
| 1 | Login to Park Street Navigator | API call — no login needed |
| 2 | Navigate to inventory section | — |
| 3 | Export CSV | — |
| 4 | Reformat spreadsheet | — |
| 5 | Run VLOOKUP for SKU mapping | — |
| 6 | Save and share file | Structured JSON returned directly |

**Time saved:** ~5 min per run, 2–3x per week = ~20–30 min/week recovered.

---

## Key SKUs Tracked (US Market)

Based on [[Cohort Analysis 2022-2026]] revenue data:

| SKU | Revenue (US) | Notes |
|---|---|---|
| J Ginjo | $2.77M | #1 US SKU |
| J DaiGinjo Noir | $2.48M | #2 |
| Junmai 12 | $1.56M | Most adopted |
| Sake Baby! | $1.22M | |
| J DaiGinjo Orange | $983K | |
| Prestige | $191K | Launched Dec 2024 |

---

## Data Quality Notes

- API returns structured JSON — no reformatting needed
- Warehouse breakdown allows visibility into which DC holds stock
- Allocated vs. available distinction prevents overselling
- Historical adjustments endpoint enables reconciliation against Xero

---

## Related Pages

- [[Park Street Navigator]]
- [[Automation Registry]]
- [[Michele Fincato]]
- [[SOP Analysis — Complete Index]]
- [[Cohort Analysis 2022-2026]]
- [[Monthly Sales Report — SOP]]
