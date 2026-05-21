---
type: infrastructure
service: Supabase
project_id: vxomboffddzpgrfhdwpd
tags: [percy, supabase, backend, edge-functions, database]
---

# Percy — Supabase Backend

> Backend for Percy: Postgres, Auth (OTP), Realtime, Storage, Edge Functions.

---

## 🔗 Connections

- **Landlord app:** [[Percy — Landlord App]]
- **Tenant PWA:** [[Percy — Tenant PWA]]
- **FinTra backend:** [[Supabase — FinTra Project]]

---

## ⚡ Edge Functions

| Function | Purpose | Auth |
|----------|---------|------|
| `create-stay` | Tenant check-in, creates stay + profile + flips room | Service role |
| `get-room-name` | Returns {id, name} for QR landing | Public |
| `get-room-details` | Returns room + amenities | Optional auth |
| `get-tenant-id-photo` | Signed URL for landlord viewing | Service role |
| `notify-checkout` | Logs checkout status (WhatsApp/push hook) | Landlord |
| `summarise-feedback` | Claude Haiku aggregation of feedback themes | Service role |

## 🗄 Database Tables

- `rooms` — name, rent, status, capacity, floor
- `stays` — tenant info, dates, checkout status + countdown
- `room_equipment` / `room_features` — amenity data
- `rentable_items` — add-ons (scooter, water, etc.) with daily rate
- `checkout_requests` — structured checkout handshake
- `bills` + `bill_items` — itemized billing
- `payments` — cash/UPI/bank tracking
- `damage_reports` — damage + complaints
- `tenant_consumables` / `consumable_types` — water etc.
- `push_tokens` — FCM for landlord notifications
- `profiles` — name, phone, type (landlord/tenant)

## 🔐 RLS Policies

Landlord-scoped CRUD on rooms/bills/payments. Tenant-scoped on stays/consumables/selections/checkout_requests.

## 📋 Migrations

34+ SQL migrations (sequential, append-only). Latest: 020 (rentable_items available column).

---

## 📋 Related

- [[Percy — Landlord App]]
- [[Percy — Tenant PWA]]
- [[Percy — Project Overview]]