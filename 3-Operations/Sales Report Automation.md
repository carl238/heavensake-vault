# Sales Report Automation

## Status: LIVE
Recurring task set up — runs on the 1st of each month at 9am CET.

## Pipeline
1. **Park Street API** → Pull US invoices for the previous month
   - Endpoint: `POST https://api.parkstreet.com/public_apis/get_invoices`
   - Auth: Token query parameter
   - Returns: Invoice line items with customer, product, qty, price, state

2. **Xero API** → Pull ROW invoices (ACCREC type, non-US markets)
   - Tenant: Lucky Sake AG (`8f11ebc0-5f31-4e70-8227-96a4bfdbf99a`)
   - Filter by date range + Type=="ACCREC"
   - Market tracking category identifies country

3. **Transform** → Map to Consolidated tab format (23 columns)
   - SKU mapping: 174 entries in `/home/user/workspace/sku_mapping.json`
   - Bottles per case: 6 (standard), 3 (Prestige), 12 (Baby 300mL)
   - Reference script: `/home/user/workspace/transform_feb2026.py`

4. **Google Sheets** → Write to spreadsheet `134V8nezw1Xyw7gJZIL76EYkMTTJHwlrNJb2sRvaNZ7o`

5. **Validate** → Compare totals against source APIs

## Feb 2026 Test Results
- US: 77 rows, 739.33 cases, $112,875.35 (exact match)
- ROW: 43 rows from 33 Xero invoices
- Total (from Summary tab): $150,832

## Known Gaps
- ROW FX conversion needs proper rates (use Summary tab values, not approximate)
- Sales Person column not available from Park Street API
- Some ROW description-only lines excluded from automated output

## Related
- [[Park Street Navigator]]
- [[Michele Fincato]]
