---
type: architecture
updated: 2026-05-22
tags: [percy, architecture, mOC]
---

# Percy System Architecture

> How Percy's landlord app, tenant PWA, and backend connect.

---

## 🔗 Architecture Diagram

```
┌──────────────────────────────────────────────────────┐
│                  LANDLORD (Flutter)                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │Dashboard │ │Room Mgmt │ │ Billing  │ │QR Gen  │ │
│  └─────┬────┘ └────┬─────┘ └────┬─────┘ └───┬────┘ │
│        └───────────┼───────────┼────────────┘       │
└────────────────────┼───────────┼────────────────────┘
                     │           │
                     ▼           ▼
┌──────────────────────────────────────────────────────┐
│                  SUPABASE                            │
│  ┌────────┐ ┌──────────────┐ ┌───────────────────┐ │
│  │Auth    │ │Edge Functions │ │Realtime           │ │
│  │(OTP)   │ │┌create-stay  │ │(room status stream│ │
│  │        │ │┌get-room-name │ │ to landlord app)  │ │
│  │        │ │┌get-room-det  │ │                   │ │
│  │        │ │┌notify-check  │ │                   │ │
│  │        │ │┌get-tenant-id │ │                   │ │
│  │        │ │┌summarise-fb  │ │                   │ │
│  └────────┘ └──────────────┘ └───────────────────┘ │
│  ┌────────────────────────────────────────────────┐ │
│  │Postgres (34+ migrations)                      │ │
│  │rooms, stays, bills, payments, damage_reports, │ │
│  │rentable_items, consumables, checkout_requests  │ │
│  └────────────────────────────────────────────────┘ │
└──────────────────────────────────────────────────────┘
                     │           │
                     ▼           ▼
┌──────────────────────────────────────────────────────┐
│              TENANT (PWA — Next.js)                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐             │
│  │Check-In  │ │Dashboard │ │Checkout  │             │
│  │(6 steps) │ │(stay mgr)│ │(5 steps) │             │
│  └──────────┘ └──────────┘ └──────────┘             │
│  URL: tenantpwa.vercel.app                          │
└──────────────────────────────────────────────────────┘
```

## 📐 QR Flow

1. Landlord creates room → app generates QR code
2. QR URL = `tenantpwa.vercel.app/room/{room_id}` (permanent, no token/expiry)
3. Tenant scans → arrives at PWA → 6-step check-in
4. Data loads fresh on every scan (no cached state)

## 🔐 Auth

- **Landlord:** Email/password (Supabase gotrue)
- **Tenant:** Phone OTP (Supabase auth)
- **Session:** localStorage (`percy_user_id`, `percy_room_id`)

---

## 📋 Related

- [[Percy — Landlord App]]
- [[Percy — Tenant PWA]]
- [[Percy — Supabase Backend]]
- [[System Architecture]]
- [[Session 2026-05-17 — Percy Auth & Add-Ons]]