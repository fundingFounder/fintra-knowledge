---
type: project
status: live
stack: Next.js, React, Tailwind, Supabase
url: https://tenantpwa.vercel.app
tags: [percy, tenant, pwa, nextjs, web]
---

# Percy — Tenant PWA

> Zero-install PWA for tenants. QR scan → check in → manage stay → checkout.

---

## 🔗 Connections

- **Landlord app:** [[Percy — Landlord App]]
- **Backend:** [[Percy — Supabase Backend]]
- **Overview:** [[Percy — Project Overview]]

---

## 📊 Tech Stack

| | |
|---|---|
| **Framework** | Next.js 16 (App Router, React 19.2) |
| **Language** | TypeScript |
| **Styling** | Tailwind CSS v4 |
| **Backend** | Supabase JS Client ^2.105.3 |
| **Icons** | Phosphor Icons React |
| **Font** | Geist |
| **Image** | browser-image-compression |
| **Testing** | Vitest + Playwright |
| **Deploy** | Vercel |
| **URL** | [tenantpwa.vercel.app](https://tenantpwa.vercel.app) |

## 📐 Key Flows

### Check-in (6 steps)
Greeting → Name+Phone → OTP Verify → Amenities Acknowledgment → Confirm+Stay/Payment Cards → Done

### Dashboard
Stay countdown, selfie/ID upload (front+rear), stay details, consumable/asset management, damage reporting, checkout request, bill display with "Settled dues" gate

### Checkout (5 steps)
Initiated screen + countdown → Departure checklist → Receipt → Farewell

## 📄 Components

CheckoutModal, ConsumableModal, AssetModal, DamageReportModal, ReportsModal, UpdateStayModal, UploadItem, AmenityTile, CtaButton, ProgressBar

## 📄 Source

- **Path:** `/Users/dibyendumondal/Unicorns/percy/product/apps/tenant_pwa/`
- **~3852 lines** across 9 page routes, 10 components, 4 lib modules

---

## 📋 Related

- [[Percy — Landlord App]]
- [[Percy — Project Overview]]