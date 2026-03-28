---
type: reference
status: needs-review
tags: [finance, receivables, AR, park-street, xero, cash]
last-updated: 2026-03-28
---

# Receivables Management

Overview of accounts receivable tracking and cash collection across US and ROW markets.

> [!warning] Needs Fresh Review
> The initial AR analysis had errors due to context overload — the "Velocity" grouping column was misread as a customer name instead of a total column. The figures below are directionally correct but should be re-validated against the source file.

---

## Current AR Position

| Field | Value |
|---|---|
| **Total Open AR** | ~$172,972 |
| **As of Date** | March 2026 |
| **Source** | Park Street Receivables Report (Feb 2026) |
| **Source File** | `Receivables-Report-as-on-February-05-2026.xlsx` |

---

## Current Process (Manual)

AR management is currently handled manually by [[Michele Fincato]]:

1. Download receivables report from Park Street Navigator
2. Review aging buckets (current, 30-day, 60-day, 90-day+)
3. Track overdue invoices via email follow-ups
4. Reconcile against Xero for ROW markets

This process has no automation and relies entirely on Michele's attention and schedule.

---

## Market Split

| Market | AR Tracking System | Notes |
|---|---|---|
| **US** | Park Street Navigator | Distributor holds and tracks receivables |
| **ROW (JP, UK, SG, etc.)** | Xero (Lucky Sake AG) | Direct invoicing via Xero |

---

## Automation Opportunity

Both data sources are API-accessible:

### Park Street (US)

Park Street API can return invoice aging data via the invoices endpoint:

```http
POST /get_invoices
```

Filtering by status and date range returns open invoices with amounts and aging.

### Xero (ROW)

```http
GET /invoices?Type=ACCREC&Status=AUTHORISED
```

Returns all outstanding ROW invoices with due dates and amounts.

### Proposed Automation

| Step | Action |
|---|---|
| 1 | Pull open US invoices from Park Street API |
| 2 | Pull open ROW invoices from Xero API |
| 3 | Combine into unified AR aging report |
| 4 | Flag invoices >30 days overdue |
| 5 | Auto-generate follow-up email drafts |
| 6 | Post summary to Google Sheets / Slack |

This would eliminate Manuel's manual weekly review and ensure consistent follow-up cadence.

---

## Open Items

- [ ] Re-analyze `Receivables-Report-as-on-February-05-2026.xlsx` with correct column mapping
- [ ] Confirm AR aging bucket definitions with Park Street (30/60/90 day)
- [ ] Determine which ROW markets are billed directly vs. through distributors
- [ ] Define escalation thresholds for overdue invoices

---

## Related Pages

- [[Financial Overview]]
- [[Park Street Navigator]]
- [[Michele Fincato]]
- [[Monthly Sales Report — SOP]]
- [[Automation Registry]]
