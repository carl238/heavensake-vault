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

## Related
- [[Sales Report Automation]]
- [[Japan Order Pipeline]]
- [[Park Street Navigator]]
- [[Michele Fincato]]
