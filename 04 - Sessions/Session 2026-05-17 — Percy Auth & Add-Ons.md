---
type: session
date: 2026-05-17
duration: long
tags: [session, percy, auth, pwa, supabase, edge-function]
---

# Session 2026-05-17 — Percy Auth & Add-Ons

> Percy tenant auth (phone OTP), consumable pending status, checkout requests, rentable items, migrations 016-020.

## 🎯 What We Did

1. **Phone-based login flow** — OTP auth to tenant PWA login page: phone lookup → OTP verify → redirect to room dashboard
2. **Phone storage fix** — `create-stay` Edge Function now receives phone from request body (not from `auth.users`)
3. **Pending consumables** — Added `status` field (pending/approved/rejected) to `tenant_consumables`; dashboard shows "Pending Requests" section
4. **Edge Function updates** — `get-room-details` works without auth (optional Authorization header)
5. **New components** — CheckoutModal, ReportsModal
6. **Migrations 016-020** — consumable pending status, consumable types RLS, damage reports RLS fix, checkout requests, rentable items RLS/available column

## 🐛 Known Issues Found

- `rentable_items_screen.dart:51` queries `landlord_id` but column is `landlord_uid`
- `ComplaintsSection` reads non-existent `stays.complaint` column
- `RequestsSection` queries non-existent `tenant_requests` table
- WhatsApp/Alerts buttons have empty `onTap: {}` handlers
- ConsumableModal hardcoded with 2 water items

## 📋 Related

- [[Percy — Tenant PWA]]
- [[Percy — Supabase Backend]]
- [[Percy System Architecture]]