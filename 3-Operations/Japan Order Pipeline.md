# Japan Order Pipeline

## Status: MONITORING ACTIVE
Email monitoring runs 3x daily on weekdays (8am, 12pm, 4pm CET).
Auto-creation of Xero quotes/POs pending approval workflow confirmation.

## Current Manual Process (Michele)
1. Nana forwards Japanese customer email to Michele
2. Michele opens Xero, copies a similar old quote as template
3. Modifies: contact, date, reference, currency (JPY), line items
4. Creates matching Purchase Order (brewery as contact, cost pricing)
5. Emails confirmation back to Nana

## Automated Pipeline (In Progress)
1. **Monitor** — Check for new Japan order emails from Nana
2. **Parse** — Extract: customer, products, quantities, delivery method
3. **Map** — Match to Xero item codes and pricing
4. **Create Quote** — Via Xero API (xero_accounting_api-make-an-api-call)
5. **Create PO** — Via Xero API, linked to quote
6. **Confirm** — Email Nana with attached PO

## Key Customers
- Imadeya Co., Ltd. (primary)
- Suzuden Co., Ltd.
- SAWAJUN International Co., Ltd.
- Sumiyoshi Shuhan Co., Ltd.

## Reference Naming Convention
- Quote: `JP_[Customer]_Order [MM]/[YYYY]_Ref. [Date]_[SKU]_SALE_[qty]btls`
- PO: `AU-[XXXXX] [SKU]-[cases] cs-JP-[MM.YYYY] | NA (api) | AIR | SALE | AU-[XXXXX] | [Customer]`

## Related
- [[Michele Fincato]]
- [[Supply Chain & Logistics]]
