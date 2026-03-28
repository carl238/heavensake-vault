---
type: reference
status: active
tags: [LIS, vanboxtel, EU, warehouse, API, logistics, portal]
last-updated: 2026-03-28
---

# LIS Logistics Portal

Full API and portal documentation for the LIS/Vanboxtel EU warehouse system (Netherlands).

---

## Portal Access

| Field | Value |
|---|---|
| **URL** | https://c3970webp01.vanboxtel.hosting/vbs-web/web-portal/ |
| **Username** | michele.fincato@heavensake.com |
| **Password** | Heavensake24! |
| **Framework** | Angular SPA (WMS Portal) |
| **Customer ID (UI)** | klant=39 |
| **Customer ID (API)** | klantId=148 |

---

## Authentication

The portal uses a two-step auth flow. External API calls are blocked by same-origin policy — authentication must be executed in the browser JS context.

### Step 1 — Get Token

```http
POST /vbs-ipc/web-portal/api/auth
Content-Type: application/json

{
  "username": "MICHELE.FINCATO@HEAVENSAKE.COM",
  "digest": "<base64(SHA-256(password + USERNAME_UPPERCASE))>"
}
```

Returns a bearer token.

### Step 2 — Create Session

```http
POST /vbs-ipc/web-portal/api/sessie
Authorization: Vanboxtel <token>
```

Returns `sessieId` required for subsequent requests.

### Working Digest (pre-computed)

```
VHvCgSjvRQLT8DIsDGjO21CjbOb3fSeq+B+xlwlEbUk=
```

> [!warning] Rotation
> Regenerate this digest if the password changes. Formula: `base64(SHA-256(password + USERNAME_UPPERCASE))`

---

## Internal API Base

```
/vbs-ipc/web-portal/api
```

> [!important] Same-Origin Restriction
> This API is only accessible from within the browser session at the portal domain. External HTTP calls (e.g., from a cron job or Python script) are blocked. All automation must execute via browser JS injection.

---

## API Endpoints

### Stock / Inventory

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/voorraad` | Current stock inventory (JSON) |
| `GET` | `/voorraad/download` | Export stock as CSV |

### Sales Orders

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/order/{id}/order-detail` | Create sales order lines |
| `PUT` | `/order/{id}/order-detail/{id}` | Update a sales order line |
| `DELETE` | `/order/{id}/order-detail/{id}` | Delete a sales order line |
| `GET` | `/ordersoort` | Retrieve available order types |

### Bulk Import

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/import/{type}/klant/{klantId}` | Bulk import (Excel data as JSON) |
| `GET` | `/import/{type}/sjabloon` | Download CSV import template |

### Other

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/factuur/{id}` | Retrieve invoice data |
| `GET` | `/recall` | Product recall data |

---

## Portal Sections

| Section | Contents |
|---|---|
| **Stock** | 19 active lines |
| **Sales Orders** | EU outbound orders |
| **Mutation Trails** | Stock movement history |
| **Pre-notifications** | Inbound shipment notifications |
| **Documents** | 4 PDFs |
| **Suppliers** | 15 registered suppliers |
| **Delivery Addresses** | 130+ EU delivery locations |
| **Articles** | 55+ registered article/SKU records |

---

## Key Insight: Write Operations Are Supported

The API supports full CRUD for sales orders — not just read. This means **EU order fulfillment can be automated programmatically**, including:

- Creating new sales order lines directly via API
- Bulk importing orders via the `/import` endpoint
- Downloading stock data on a schedule (already live as daily cron)

The primary limitation is the same-origin policy, which requires any automation to run via browser JS context rather than a standalone external script.

---

## Automation Status

| Process | Status |
|---|---|
| EU Stock Report Download | ✅ AUTOMATED — daily cron live |
| EU Sales Order Creation | 🔧 READY TO BUILD |
| Custom Clearance Request | 🔵 PARTIALLY AUTOMATED (40%) |

See [[SOP Analysis — Complete Index]] for full process breakdown.

---

## Related Pages

- [[Supply Chain & Logistics]]
- [[EU Inventory Management]]
- [[Michele Fincato]]
- [[Automation Registry]]
- [[SOP Analysis — Complete Index]]
