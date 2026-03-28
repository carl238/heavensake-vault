---
type: reference
status: active
tags: [shipping, forwarders, logistics, quotation, automation]
last-updated: 2026-03-28
---

# Forwarder & Shipping Management

Documentation for the international shipping quotation process and freight forwarder management.

---

## Process Overview

**Frequency:** 3–5 shipments per month
**Automation Level:** 50%
**Status:** 🔵 PARTIALLY AUTOMATED — Tools built, human judgment required for quote selection

---

## End-to-End Shipping Workflow

| Step | Action | Automated? |
|---|---|---|
| 1 | Confirm production with brewery | ❌ Manual |
| 2 | Create Xero Purchase Order | ❌ Manual |
| 3 | Create Park Street shipment request | ❌ Manual (no API) |
| 4 | Generate forwarder quote request email | ✅ Automated (`generate_shipping_email.py`) |
| 5 | Send emails to forwarder list | ❌ Manual send |
| 6 | Collect quotes from forwarders | ❌ Manual (email) |
| 7 | Build quote comparison | ✅ Template built (`forwarder_quote_template.csv`) |
| 8 | Select forwarder | ❌ Human judgment required |
| 9 | Confirm shipment with selected forwarder | ❌ Manual |

> [!note] Park Street Limitation
> Park Street has no shipment creation API. Steps 3 and 9 require manual portal interaction.

---

## Automation Tools Built

### `generate_shipping_email.py`

Generates forwarder quote request emails from Xero PO data:
- Pulls PO details (origin, destination, dimensions, weight, HS codes)
- Formats into standard quote request template
- Outputs ready-to-send email body per forwarder

### `forwarder_quote_template.csv`

Google Sheets comparison template for collecting and comparing forwarder quotes:
- Columns: Forwarder | Origin | Destination | Mode | Transit Time | Total Cost (USD) | Validity | Notes
- Supports side-by-side comparison of 3–8 forwarders per shipment

### `forwarder_contacts.json`

> [!warning] Needs Real Data
> This file currently contains **placeholder data**. Real forwarder contact details must be provided by Michele. The file structure is ready; it just needs to be populated.

---

## LSK Shipment ID Tracking

Shipment IDs are auto-tracked via Airtable:

| Field | Value |
|---|---|
| **Airtable Table** | Shipments |
| **Table ID** | `tblTdHw3iDPWX8VIM` |
| **Current Max LSK ID** | LSK246 |
| **Behavior** | Auto-increments for each new shipment |

Format: `LSK{number}` — e.g., LSK246, LSK247, LSK248...

---

## Freight & Logistics Partners

For the full list of freight and logistics partners, see:

[[Supply Chain & Logistics#Freight & Logistics Partners]]

---

## Remaining Automation Gaps

| Gap | Impact | Priority |
|---|---|---|
| Populate `forwarder_contacts.json` | Required for email automation | High |
| Park Street shipment creation | Must stay manual | Blocked (no API) |
| Quote collection from forwarders | Requires email parsing or forwarder portal API | Medium |
| Forwarder selection | Requires human judgment on cost/speed tradeoff | Will remain manual |

---

## Related Pages

- [[Supply Chain & Logistics]]
- [[Michele Fincato]]
- [[Automation Registry]]
- [[SOP Analysis — Complete Index]]
- [[Japan Order Pipeline]]
