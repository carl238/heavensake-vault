---
type: reference
status: active
tags: [sop, processes, automation, michele, operations]
last-updated: 2026-03-28
---

# SOP Analysis — Complete Index

All 8 Michele operational processes analyzed from video SOPs. This index tracks automation status, time savings, and links to supporting documentation.

---

## Impact Summary

| Metric | Before | After | Savings |
|---|---|---|---|
| **Monthly Hours** | ~41 hrs | ~7.25 hrs | **~33.75 hrs (82% reduction)** |

---

## Process Index

### Process 1 — Custom Clearance Request (EU/LIS)

| Field | Detail |
|---|---|
| **Duration** | 2:58 |
| **Frequency** | As needed |
| **Systems** | LIS Portal ([[LIS Logistics Portal]]), Email |
| **Automation Level** | 40% |
| **Status** | 🔵 PARTIALLY AUTOMATED |

**Steps:** Check bonded inventory in LIS → identify pallets ready for clearance → draft clearance request email → send to LIS team.

Remaining manual work: pallet selection and email send still require human judgment. Email templating is automated.

---

### Process 2 — EU Stock Report Download (LIS)

| Field | Detail |
|---|---|
| **Duration** | 4:54 |
| **Frequency** | 2–3x per week |
| **Systems** | LIS Portal ([[LIS Logistics Portal]]), Google Sheets |
| **Automation Level** | 95% |
| **Status** | ✅ AUTOMATED — Live daily cron (job: `6bdeef94`) |

**Steps:** Login to LIS → navigate to Stock → download CSV → classify by status (Cleared/Bonded) → update tracker → alert if Cleared <50 bottles.

Fully automated. Cron runs daily and sends alerts when cleared stock falls below threshold.

---

### Process 3 — Japan SO/PO Creation (Xero)

| Field | Detail |
|---|---|
| **Duration** | 4:47 |
| **Frequency** | Per order |
| **Systems** | Xero, [[Japan Order Pipeline]] |
| **Automation Level** | 80% |
| **Status** | 👁️ MONITORING — Checks 3x daily |

**Steps:** Receive Japan order → create Xero quote → convert to sales order → create purchase order → confirm with brewery → track shipment.

Monitoring runs 3x daily. Remaining manual work: brewery confirmation and edge-case handling.

---

### Process 4 — US Stock Report (Park Street)

| Field | Detail |
|---|---|
| **Duration** | 5:00 |
| **Frequency** | 2–3x per week |
| **Systems** | Park Street API ([[Park Street Navigator]]) |
| **Automation Level** | 100% |
| **Status** | ✅ FULLY AUTOMATED |

**Steps (old manual):** Login Park Street → export CSV → reformat → VLOOKUP → save.

Now replaced entirely by `POST /get_product_inventory_snapshot` API call. Returns structured per-SKU data with warehouse breakdown. See [[US Inventory — Park Street]].

---

### Process 5 — EU Sales Orders (LIS)

| Field | Detail |
|---|---|
| **Duration** | 4:54 |
| **Frequency** | 10–15 orders per month |
| **Systems** | LIS Portal ([[LIS Logistics Portal]]) |
| **Automation Level** | 80% |
| **Status** | 🔧 READY TO BUILD |

**Steps:** Receive EU order → log into LIS → create sales order → add order lines → confirm.

API supports write operations (`POST /order/{id}/order-detail`). Build path is clear; implementation pending.

---

### Process 6 — Sales Invoice Issuance (JP/Asia/UAE/CAN)

| Field | Detail |
|---|---|
| **Duration** | 4:31 |
| **Frequency** | Weekly + per shipment |
| **Systems** | Xero |
| **Automation Level** | 95% |
| **Status** | ✅ AUTOMATED — Cron live |

**Steps:** Identify shipped orders → create Xero invoice → apply correct currency/tax settings → send to customer.

Xero API handles invoice creation. Cron runs on schedule. Covers JP, Asia, UAE, CAN markets.

---

### Process 7 — Shipping Quotation Requests

| Field | Detail |
|---|---|
| **Duration** | 11:29 (longest process) |
| **Frequency** | 3–5 per month |
| **Systems** | Xero, Park Street, Email, Airtable |
| **Automation Level** | 50% |
| **Status** | 🔵 PARTIALLY AUTOMATED — Tools built |

**Steps:** Confirm production → create Xero PO → create Park Street shipment request → generate forwarder email → send to forwarders → collect quotes → build comparison → select forwarder → confirm.

Tools built: `generate_shipping_email.py` and `forwarder_quote_template.csv`. Quote selection requires human judgment. See [[Forwarder & Shipping Management]].

---

### Process 8 — Monthly Sales Report

| Field | Detail |
|---|---|
| **Duration** | (varies) |
| **Frequency** | Monthly (1st of month, 9am CET) |
| **Systems** | Park Street API, Xero API, Google Sheets |
| **Automation Level** | 95% |
| **Status** | ✅ AUTOMATED — Cron `f4d79933` |

Full pipeline: Park Street → Xero → Transform → Google Sheets → Validate. See [[Monthly Sales Report — SOP]] for complete documentation.

---

## Automation Status Legend

| Icon | Status | Meaning |
|---|---|---|
| ✅ | AUTOMATED | Running in production |
| 👁️ | MONITORING | Automated checks active |
| 🔧 | READY TO BUILD | Design complete, not yet implemented |
| 🔵 | PARTIALLY AUTOMATED | Some steps automated |

---

## Related Pages

- [[Michele Fincato]]
- [[Automation Registry]]
- [[LIS Logistics Portal]]
- [[Japan Order Pipeline]]
- [[Park Street Navigator]]
- [[EU Inventory Management]]
- [[US Inventory — Park Street]]
- [[Forwarder & Shipping Management]]
- [[Monthly Sales Report — SOP]]
