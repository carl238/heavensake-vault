# Automation Registry

## Active Recurring Tasks

| ID | Name | Schedule | Status |
|---|---|---|---|
| f4d79933 | Monthly Sales Report | 1st of month, 9am CET | ACTIVE |
| dc164f40 | Japan Order Monitor | 3x daily, weekdays | ACTIVE |
| 6bdeef94 | EU Stock Report (LIS) | Daily, weekdays 8am | ACTIVE |
| a9c4ca18 | Auto-Invoice (Shipped POs) | 2x daily, weekdays 10am+4pm | ACTIVE |

## Utility Scripts

| Script | Purpose | Location |
|---|---|---|
| check_eu_stock.py | Check EU inventory status from LIS CSV | /home/user/workspace/ |
| check_eu_stock_for_order.py | Verify order can be fulfilled from cleared stock | /home/user/workspace/ |
| generate_shipping_email.py | Generate forwarder quote request email from PO data | /home/user/workspace/ |
| transform_feb2026.py | Transform Park Street + Xero data for sales report | /home/user/workspace/ |

## Connected APIs

| System | Type | Status |
|---|---|---|
| Park Street | REST API (token) | LIVE — 4 endpoints |
| Xero | OAuth connector | LIVE — full CRUD |
| Google Sheets | OAuth connector | LIVE |
| Airtable | OAuth connector | LIVE |
| LIS Logistics | Reverse-engineered API | CONFIRMED — same-origin only |
| Gmail | OAuth connector | LIVE |
| Slack | Direct connector | LIVE |

## Airtable Key Tables

| Table | ID | Purpose |
|---|---|---|
| PurchaseOrders(XERO) | tblnQXZ54DOSbfngb | Invoicing trigger — has ship date + quote ref |
| Shipments | tblTdHw3iDPWX8VIM | LSK shipment tracking — current max: LSK246 |
| SKUs | tbl9Z3NtXVKifwMwV | Centralized SKU mapping |
| XeroQuotes | tblRG9GbeGvIisTpV | Quote references (AU-XXXXX) |
| Parsed_Email_Orders | tblf9SVkQncKkoPR6 | AI email order parsing staging |

## Configuration Files

| File | Purpose |
|---|---|
| forwarder_contacts.json | Forwarder names, emails, route specialties — NEEDS REAL DATA |
| sku_mapping.json | 174-entry SKU → product name/brewery mapping |
| lis_credentials.json | LIS portal auth details |

## Automation Tools (Built March 2026)

| Tool | What It Does | Trigger |
|---|---|---|
| Auto-Invoice (Shipped POs) | Detects shipped POs in Airtable → finds Xero quote → creates invoice → writes ref back | Cron a9c4ca18, 2x daily |
| EU Stock Checker | Downloads LIS CSV → classifies bonded/cleared → alerts on low stock | Cron 6bdeef94, daily 8am |
| EU Stock for Order | Verifies specific order can be fulfilled from cleared EU stock | On-demand script |
| Shipping Email Generator | Generates forwarder quote request email from PO data | On-demand script |
| LSK ID Auto-Assignment | Tracks max LSK shipment ID in Airtable, auto-increments | Built into auto-invoice flow |
| Forwarder Quote Comparison | Persistent Google Sheet template for comparing forwarder quotes | Manual |

## Perplexity Computer vs Make.com

Two automation layers now run in parallel:

| Layer | What It Handles | Strengths |
|---|---|---|
| **Make.com** ([[Ops & Automations — Make.com]]) | Nightly Xero/Airtable syncs, dashboards, shipment ETA tracking, JP brewery forms | Real-time webhooks, Airtable writes, established flows |
| **Perplexity Computer** | Sales report generation, auto-invoicing, EU stock monitoring, Japan order detection | API orchestration, multi-system logic, AI-powered parsing |

Both complement each other — Make.com handles continuous sync, Perplexity handles complex multi-step workflows.

## Impact Summary

- **Before automation:** ~41 hrs/month of Michele's operational time
- **After automation:** ~7.25 hrs/month
- **Savings:** ~34 hrs/month (82% reduction) — one full work week recovered per month
- See [[SOP Analysis — Complete Index]] for per-process breakdown

## Related
- [[Sales Report Automation]]
- [[Japan Order Pipeline]]
- [[Park Street Navigator]]
- [[Michele Fincato]]
- [[SOP Analysis — Complete Index]]
- [[LIS Logistics Portal]]
- [[Monthly Sales Report — SOP]]
- [[EU Inventory Management]]
- [[US Inventory — Park Street]]
- [[Forwarder & Shipping Management]]
