---
type: sop
status: active
tags: [sales-report, automation, park-street, xero, google-sheets, monthly]
last-updated: 2026-03-28
---

# Monthly Sales Report — SOP

Automated pipeline that consolidates US and ROW invoice data into the monthly sales report Google Sheet.

---

## Pipeline Overview

```
Park Street API (US)
        ↓
    Xero API (ROW)
        ↓
  Transform & Map SKUs
        ↓
  Google Sheets (Consolidated tab)
        ↓
    Validate & Alert
```

**Schedule:** 1st of each month at 9:00 AM CET
**Cron Job ID:** `f4d79933`
**Spreadsheet ID:** `134V8nezw1Xyw7gJZIL76EYkMTTJHwlrNJb2sRvaNZ7o`
**Reference Script:** `transform_feb2026.py`

---

## Data Sources

### Source 1 — Park Street API (US Invoices)

```http
POST https://api.parkstreet.com/public_apis/get_invoices
```

Parameters: date range (first day to last day of prior month)

Returns:
- `invoice_num`
- `customer` (buyer name)
- `state` (US state)
- Line items: SKU, quantity, unit price, extended price

### Source 2 — Xero API (ROW Invoices)

```http
GET /invoices?Type=ACCREC
```

Filter: `ACCREC` type + date range → then exclude US/Park Street contacts to isolate ROW data.

**ROW markets covered:** JP, LB, MY, SG, TH, TW, UAE, UK

---

## Transformation Logic

| Step | Action |
|---|---|
| 1 | Map SKUs via `sku_mapping.json` (174 entries) |
| 2 | Calculate cases: `bottles ÷ bottles_per_case` |
| 3 | Format dates to standard format |
| 4 | Assign `Source` field: `"YYYY.MM US"` or `"YYYY.MM ROW"` |
| 5 | Populate all 23 columns in Consolidated tab |

---

## Consolidated Tab — Column Structure (23 columns)

| # | Column | Source |
|---|---|---|
| 1 | Source | Derived (YYYY.MM US / ROW) |
| 2 | Date | Invoice date |
| 3 | Doc type | Invoice type |
| 4 | Client | Customer name |
| 5 | State | US state (US only) |
| 6 | Customer Type | From contact data |
| 7 | Sales Person | ⚠️ Not from API — manual field |
| 8 | Product id | Internal product ID |
| 9 | SKU | Mapped via `sku_mapping.json` |
| 10 | SKU x Brewery | SKU + brewery combination |
| 11 | Brewery | Brewery name |
| 12 | Description | Product description |
| 13 | Warehouse | Fulfillment warehouse |
| 14 | Is sample | Boolean |
| 15 | Cases Qty | Calculated |
| 16 | Sales amount (USD) | Invoice line value |
| 17 | Bottles Qty | From invoice |
| 18 | Country code | ISO country code |
| 19 | Country | Full country name |
| 20 | Year | Derived from date |
| 21 | Quarter | Derived from date |
| 22 | Month | Derived from date |
| 23 | Year & Month | Combined field |

---

## Validation Step

After data load, the pipeline runs validation checks:

| Check | Method |
|---|---|
| US row count & totals | Compare against Park Street API summary |
| ROW row count | Count rows by source |
| SKU mapping failures | Report unmapped SKUs |
| Case calculation accuracy | Spot-check against known products |

---

## February 2026 Test Results

| Metric | US | ROW | Total |
|---|---|---|---|
| **Rows** | 77 | 43 | 120 |
| **Cases** | 739.33 | — | — |
| **Revenue** | $112,875.35 | ~$37,957 | **~$150,832** |
| **Accuracy** | ✅ Exact match | — | Per Summary tab |

ROW data covered 33 Xero invoices across 8 markets.

---

## Known Gaps & Limitations

| Gap | Details |
|---|---|
| **ROW FX conversion** | FX rates should come from Summary tab, not hardcoded |
| **Sales Person column** | Not available from any API — requires manual population or Xero contact enrichment |
| **ROW description-only lines** | 59 rows in sheet vs. 43 automated — some ROW description-only lines are excluded by current filters |
| **SKU mapping completeness** | `sku_mapping.json` has 174 entries; new SKUs need to be added manually when launched |

---

## Related Pages

- [[Park Street Navigator]]
- [[Automation Registry]]
- [[Sales Report Automation]]
- [[Cohort Analysis 2022-2026]]
- [[SOP Analysis — Complete Index]]
- [[Michele Fincato]]
