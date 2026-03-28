# Park Street Navigator

## Overview
Park Street is HEAVENSAKE's US importer platform (Lucky Sake account). It manages sales orders, invoicing, inventory, shipments, compliance, and financial reporting for all US market operations.

**Platforms:**
- New UI: `app.parkstreet.com`
- Legacy: `navigator.parkstreet.com`

## Key URLs

| Section | URL |
|---------|-----|
| Dashboard | `app.parkstreet.com/dashboard` |
| Sales Orders | `app.parkstreet.com/sales-orders` |
| Sales Invoice Report | `app.parkstreet.com/sales-invoice-report?startDate=YYYY-MM-DD&endDate=YYYY-MM-DD` |
| Invoice Management | `app.parkstreet.com/invoice-management` |
| Balance Account | `app.parkstreet.com/balance-account` |
| Inventory | `app.parkstreet.com/inventory-transactions` |
| Shipments | `app.parkstreet.com/shipments` |
| Products | `app.parkstreet.com/product-tool` |
| AR Reports | `app.parkstreet.com/accounts-receivable/ar-reports` |
| Bill Management | `app.parkstreet.com/bill-management` |

## Public API
- **Base URL:** `https://api.parkstreet.com/public_apis/`
- **Documentation:** https://parkstreet.readme.io/reference/getinvoices-2
- **Swagger docs:** `navigator.parkstreet.com/router.php/public_apis`
- **OpenAPI spec:** `navigator.parkstreet.com/js/public_apis.json`
- **Auth:** Token as query parameter `?token=f25e6217724e35a33a8fc80e723741bfea944553`
- **All methods:** POST with JSON body `{"date_from": "YYYY-MM-DD", "date_to": "YYYY-MM-DD"}`

### Tested & Working Endpoints (March 2026)
| Endpoint | Method | Purpose | Data Returned |
|----------|--------|---------|---------------|
| `/get_invoices` | POST | US invoices by date range | invoice_num, customer, state, line items with SKU/qty/price |
| `/get_sales_order` | POST | US sales orders by date range | order status, shipping address, line items |
| `/inventory_adjustment` | POST | Per-product transaction history | Requires product + date range |
| `/get_product_inventory_snapshot` | POST | Current inventory by SKU | Warehouse breakdown, on-hand, available, allocated |

### Additional API Endpoints (from Swagger)
| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/get_data/sales_order` | POST | Pull sales order data |
| `/set_data/sales_order` | POST | Create/update sales orders |
| `/get_data/expense_report` | POST | Pull expense data |
| `/get_data/cash_report` | POST | Pull cash/balance data |
| `/set_data/purchase_order` | POST | Create purchase orders |
| `/set_data/transfer_order` | POST | Create transfer orders |
| `/credit_management` | POST | Pull credit memos |

## Export Options
All key sections support CSV/Excel export. Sales Invoice Report and Invoice Management support URL-based date filtering — ideal for automation.

## Data in System (as of March 2026)
- 4,043 sales orders (7,829 line items), $11.4M total historical
- 105 product SKUs
- 87 inventory product-location combinations
- 325 shipments
- 1,126 invoices ($172,972 open AR)

## Key Contacts
- **Zak Gross** — Park Street account manager
- **depletions@parkstreet.com** — for VIP depletion data issues

## Users (as of March 2026)
- carl (Admin, Full Access)
- Automation Heavensake
- Michele Fincato
- Nana Zomen
- Sebastien L'Hermitte
- Sunidhi K
- Zak Gross

## Automation Integration

Park Street API is now the backbone of two automated workflows:
1. **Monthly Sales Report** ([[Monthly Sales Report — SOP]]) — pulls US invoices on 1st of each month
2. **US Inventory Tracking** ([[US Inventory — Park Street]]) — structured data replaces manual CSV exports

See [[Automation Registry]] for all active tasks.

## Related
- [[Supply Chain & Logistics]]
- [[Michele Fincato]]
- [[Monthly Sales Report — SOP]]
- [[US Inventory — Park Street]]
- [[Automation Registry]]
- [[Cohort Analysis 2022-2026]]
