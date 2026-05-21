---
type: project-overview
status: active
tags: [mOC, percy, startup]
---

# 🏠 Percy — Project Overview

> **QR-first PG room management for Indian landlords.** Scan → Check in → Manage → Checkout.

---

## 🏗 The Two Surfaces

| Surface | Tech | URL | Status |
|---------|------|-----|--------|
| [[Percy — Landlord App\|Landlord App]] | Flutter + Dart (Android/APK) | Sideload APK | Beta |
| [[Percy — Tenant PWA\|Tenant PWA]] | Next.js 16 + Tailwind | [tenantpwa.vercel.app](https://tenantpwa.vercel.app) | Live |
| [[Percy — Supabase Backend\|Backend]] | Supabase (Postgres + Edge Functions) | Project: `vxomboffddzpgrfhdwpd` | Live |

---

## 🔗 How It Connects

```
┌─────────────────────────────────────┐
│  Landlord (Flutter App)            │
│  ┌───────┐  ┌──────┐  ┌────────┐  │
│  │Dashboard│  │Rooms │  │Billing │  │
│  └───┬─────┘  └──┬───┘  └───┬────┘│
└──────┼────────────┼──────────┼─────┘
       │            │          │
       ▼            ▼          ▼
┌─────────────────────────────────────┐
│        SUPABASE                    │
│  ┌────────┐ ┌──────────────┐      │
│  │Auth     │ │Edge Functions│      │
│  │(OTP)   │ │create-stay   │      │
│  │        │ │get-room-*     │      │
│  │        │ │notify-checkout│      │
│  └────────┘ └──────────────┘      │
└─────────────────────────────────────┘
       │            │
       ▼            ▼
┌─────────────────────────────────────┐
│  Tenant (PWA)                      │
│  ┌───────┐  ┌────────┐  ┌──────┐  │
│  │Check-In│  │Dashboard│  │Checkout│ │
│  └────────┘  └────────┘  └──────┘  │
└─────────────────────────────────────┘
```

---

## 💰 Pricing

- **Free tier:** 5 rooms
- **₹499/room/month**
- **₹2000/5-room bundle**
- Demo-first, India-first, Goa launch

---

## 🐛 Known Issues

- `rentable_items_screen.dart:51` → queries `landlord_id` but column is `landlord_uid`
- `ComplaintsSection` reads non-existent `stays.complaint` column
- `RequestsSection` queries non-existent `tenant_requests` table
- WhatsApp/Alerts buttons have empty `onTap: {}` handlers
- No Flutter UI for landlord to view damage reports

---

## 📋 Related

- [[Percy — Landlord App]]
- [[Percy — Tenant PWA]]
- [[Percy — Supabase Backend]]
- [[Percy — Design System]]
- [[Session 2026-05-22 — Admin Email System]]
- [[Session 2026-05-17 — Percy Auth & Add-Ons]]