---
type: reference
status: active
tags: [inventory, EU, warehouse, LIS, logistics, stock]
last-updated: 2026-03-28
---

# EU Inventory Management

EU warehouse stock management via LIS Logistics / Vanboxtel (Netherlands).

---

## Warehouse Details

| Field | Value |
|---|---|
| **Operator** | LIS Logistics (Vanboxtel) |
| **Location** | Netherlands |
| **Portal** | [[LIS Logistics Portal]] |
| **Customer ID** | klant=39 (UI) / klantId=148 (API) |

---

## Inventory Status Types

EU inventory is held in two states:

| Status | Description | SKU Suffix | Notes |
|---|---|---|---|
| **Cleared** | Duty-paid, ready to sell | `-EU` | Available for immediate EU sales orders |
| **Bonded** | Under customs bond | `-EUB`, `-B` | Pending clearance request; cannot be sold until cleared |

---

## Stock Snapshot — March 26, 2026

### Cleared Stock (915 bottles total)

| SKU | Product | Bottles | Status |
|---|---|---|---|
| LSK-JGD-720-0325-EU | J Ginjo Dewazakura | 467 | 🟢 GREEN |
| LSK-J12-720-0224-EU | Junmai 12 | 192 | 🟢 GREEN |
| LSK-J12-720-0325-EU | Junmai 12 | 101 | 🟢 GREEN |
| LSK-JDOS-720-1124-EU | J DaiGinjo Orange | 60 | 🟡 YELLOW |
| LSK-JDAIGSA-720 | J DaiGinjo | 30 | 🟡 YELLOW |
| Others | Various | <20 each | 🔴 RED |

### Bonded Stock (2,400 bottles total)

| SKU | Product | Bottles |
|---|---|---|
| LSK-BABY-300-924-EUB | Sake Baby! | 501 |
| LSK-JDNNIIZ-720-0325-EUB | J DaiGinjo Noir Niizawa | 480 |
| LSK-JGD-720-0325-EUB | J Ginjo Dewazakura | 434 |
| LSK-JDOS-720-1124-EUB | J DaiGinjo Orange | 925 |
| LSK-AP1N-720-1025B | Prestige Noguchi | 60 |

---

## Stock Status Color Coding

| Color | Threshold | Meaning |
|---|---|---|
| 🟢 GREEN | >100 bottles | Healthy — no action needed |
| 🟡 YELLOW | 20–100 bottles | Monitor — plan clearance |
| 🔴 RED | <20 bottles | Critical — immediate clearance required |

---

## Clearance Workflow

When cleared stock falls into YELLOW or RED, bonded stock must be cleared through customs:

1. Log into [[LIS Logistics Portal]]
2. Navigate to Stock → view bonded inventory
3. Select pallets to clear (match to SKUs needing replenishment)
4. Send clearance request email to LIS team
5. LIS processes customs paperwork; SKU status changes from `EUB` → `EU`

> [!tip] Automation Note
> Step 4 (email generation) is 40% automated — see Process 1 in [[SOP Analysis — Complete Index]].

---

## Automated Monitoring

A daily cron job handles EU stock monitoring automatically:

| Field | Value |
|---|---|
| **Cron Job ID** | `6bdeef94` |
| **Schedule** | Daily |
| **Action** | Downloads stock CSV via `GET /voorraad/download` |
| **Classification** | Assigns GREEN/YELLOW/RED per bottle count |
| **Alert Trigger** | Cleared stock <50 bottles on any SKU |
| **SOP Reference** | Process 2 — [[SOP Analysis — Complete Index]] |

This replaces Michele's manual 2–3x/week stock check process (Process 2 in SOPs).

---

## Clearance Planning — Key Observations

- **Sake Baby!** (501 bonded) and **J DaiGinjo Orange** (925 bonded) represent the largest pending clearance volumes
- **J DaiGinjo Noir Niizawa** (480 bonded) is a newer SKU — priority clearance timing TBD
- Cleared J DaiGinjo Orange (60) and J DaiGinjo (30) are in YELLOW — should trigger near-term clearance requests

---

## Related Pages

- [[LIS Logistics Portal]]
- [[Supply Chain & Logistics]]
- [[Michele Fincato]]
- [[Automation Registry]]
- [[SOP Analysis — Complete Index]]
