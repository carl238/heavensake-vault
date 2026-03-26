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
- Swagger docs: `navigator.parkstreet.com/router.php/public_apis`
- OpenAPI spec: `navigator.parkstreet.com/js/public_apis.json`
- Auth: Company token (query param `?token=XXX`) — must be requested from Park Street

### API Endpoints
| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/public_apis/get_data/sales_order` | POST | Pull sales order data |
| `/public_apis/set_data/sales_order` | POST | Create/update sales orders |
| `/public_apis/get_data/expense_report` | POST | Pull expense data |
| `/public_apis/get_data/cash_report` | POST | Pull cash/balance data |
| `/public_apis/set_data/purchase_order` | POST | Create purchase orders |
| `/public_apis/set_data/transfer_order` | POST | Create transfer orders |
| `/public_apis/credit_management` | POST | Pull credit memos |

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

## Related
- [[Supply Chain & Logistics]]
- [[Michele Fincato]]
