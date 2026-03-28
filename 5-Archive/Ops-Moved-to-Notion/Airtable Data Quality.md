---
type: knowledge
status: active
last-synthesized: 2026-03-28
source-sessions:
  - Perplexity Computer session March 25-28 2026
tags: [airtable, data-quality, operations, automation]
---

# Airtable Data Quality

Reference for the HEAVENSAKE Operations Airtable base (`app5cYjK919CA4hUR`) — current data quality status, known issues, and standards.

> **Automated monitoring:** A weekly data quality check runs every Monday at 9am CET via Perplexity Computer, emailing findings to Carl. See [[Automation Registry]] for full schedule.

---

## Overall Quality Score: 55/100

Based on audit conducted March 23-27, 2026 across all key tables.

---

## Base Structure

| Base | ID | Role |
|---|---|---|
| **HEAVENSAKE Operations** | app5cYjK919CA4hUR | Main operations database (28 tables) |
| **Production & Inventory Management** | app4m0Bf0UmYIVN35 | Legacy base — inventory not yet migrated |
| **Pricing** | appt39wuor9p7QikB | Pricing data — no Notion documentation exists |

---

## Key Tables & Known Issues

### Invoices (tblOfrVyTnrmuBtdU)

- **120 invoices** missing market/zone tracking category (as of March 2026)
- Affects ALL markets, not just historical records
- Root cause: Xero tracking category not flowing through Make.com import, or lookup chain from Invoice → InvoiceLineItems → Market breaking
- **Impact:** Revenue-by-market reporting is the single most important analytics dimension

### SKUs (tbl9Z3NtXVKifwMwV)

- **27 records** with empty `skus_id` field
- **25 groups** of duplicate SKU identifiers
- **9 records** orphaned (not linked to any product)
- **Decision pending:** Should batch-level SKUs (with bottling date suffix like "-1023") be separate records?
- **SKU format standard:** `LSK-[Product 3-char]-[Brewery 3-char]-[Size 1-char]`

### Product_Master_Table (tbluHBO31m16J0ctJ)

- 4 shell records with no product names
- 3 active products have no linked SKUs:
  - LSK-JDN-DEW-S — Junmai Daiginjo Label Noir x Dewazakura (720mL)
  - LSK-JGA-SHI-M — Junmai Ginjo Label Azur x Shichiken (1500mL) — new, added Feb 2026
  - LSK-AP3-NOG-S — Assemblage Prestige1 x Noguchi — CN market only
- 2 duplicate EAN barcodes: AP1/PP1 Noguchi share one; AP2/PP2 Niizawa share another — active shipment risk

### PurchaseOrders(XERO) (tblnQXZ54DOSbfngb)

- **285 stale POs** — not modified in >14 days, still in AUTHORISED/SUBMITTED status
- Root cause: Xero housekeeping — delivered POs never moved to BILLED/CLOSED
- **SAMPLE vs SAMPLES** coexist as separate values (71 records) — corrupts type-based reporting
- 9 non-standard PO IDs with suffix letters (e.g., PO-00114a/b/o)
- 78 records (26.3%) have blank `sample_or_sale` — concentrated in Dewazakura

### Suppliers (tbluoUIRXRRD9bshP)

- 3 active suppliers missing FDA numbers: Shichiken, Niizawa, Dewazakura
- Leading whitespace in Xero contact IDs for Noguchi and Dewazakura
- Katsuyama has placeholder KAT-001 instead of real Xero UUID

### Distributors

- 98% of records missing `xero_contact_id`, `primary_contact_person`, `coverage_area`, `payment_terms`
- 74% have no market linkage
- Contains invalid entries (gift cards, personal names filed as companies)
- Essentially an unprocessed migration dump

### Brewery_inventory_reports (tblSakvBwGRnpvNE1)

- 6 Japanese breweries should submit monthly
- Historical response rate: 5/6 (83%)
- NIIZAWA is the consistent non-respondent via form — but did submit manually in January 2026 (usability issue, not engagement issue)

---

## Connector Limitation

The Pipedream Airtable connector (`airtable_oauth__pipedream`) **cannot update existing records** — the `update-record` component uses `additionalProps()` which the connector service doesn't call. Field-level updates require either:
1. Airtable Personal Access Token for direct API calls
2. A full Pipedream workflow with component-level additionalProps() support

This affects all 144 records missing `invoice_type`, `created_by`, `updated_by`, and `is_active` fields.

---

## Monitoring Schedule

See [[Automation Registry]] for full details. Key checks:
- **Weekly (Mondays):** Full data quality scan of 6 tables — invoices, POs, products, SKUs, suppliers, brewery reports
- **Monthly (5th):** Invoice-to-product linkage validation, SKU orphan detection
- All findings delivered via email to Carl

---

## Related

- [[Automation Registry]]
- [[Tech & Automation Stack]]
- [[Ops & Automations — Make.com]]
- [[Michele Fincato]]
- [[Monthly Sales Report — SOP]]
