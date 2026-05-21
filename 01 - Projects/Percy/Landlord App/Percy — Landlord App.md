---
type: project
status: beta
stack: Flutter, Dart, Supabase
platform: Android (APK sideload)
tags: [percy, landlord, flutter, mobile]
---

# Percy — Landlord App

> Native Flutter app for PG landlords. Room management, QR generation, billing, checkout.

---

## 🔗 Connections

- **Backend:** [[Percy — Supabase Backend]]
- **Tenant side:** [[Percy — Tenant PWA]]
- **Overview:** [[Percy — Project Overview]]

---

## 📊 Tech Stack

| | |
|---|---|
| **Framework** | Flutter (Dart SDK ^3.11.5) |
| **Backend** | Supabase (auth, realtime, storage) |
| **Navigation** | Go Router ^14.8.1 |
| **Fonts** | Google Fonts (Inter, Montserrat) |
| **Icons** | Phosphor Flutter |
| **QR** | qr_flutter, share_plus, printing |

## 📐 Key Screens

- **Dashboard** — 2-column room grid (Vacant/Occupied/Needs Attention), realtime stream
- **Room Detail** — 4 tabs: Overview, Requests, Finance, Settings
- **Create Room** — 16 amenity toggles (8 equipment + 8 features)
- **Rentable Items** — CRUD for add-ons with daily rate toggle
- **Bill Preview** — Auto-calculate, edit lines, custom charges
- **Bill Status** — Payment tracking, mark paid, complete checkout
- **Checkout Handshake** — Initiate/complete, countdown, extension, feedback

## 📄 Source

- **Path:** `/Users/dibyendumondal/Unicorns/percy/product/apps/percy_app/`
- **19 Dart files, ~6053 lines**
- **Largest:** `dashboard_screen.dart` (928 lines), `bill_preview_screen.dart` (555 lines)

---

## 📋 Related

- [[Percy — Project Overview]]
- [[Percy — Tenant PWA]]