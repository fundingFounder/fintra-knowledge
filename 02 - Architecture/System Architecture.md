---
type: architecture
updated: 2026-05-22
tags: [architecture, mOC]
---

# System Architecture

> How everything connects across ALL projects on this machine.

---

## 🔗 FinTra Ecosystem

```
┌─────────────────────────────────────────────────────┐
│               USERS                                 │
│  ┌──────────┐  ┌──────────┐  ┌──────────────────┐ │
│  │ App User │  │ App User │  │ Admin (Dibyendu) │ │
│  │(Mobile)  │  │(Mobile)  │  │Dashboard         │ │
│  └────┬─────┘  └────┬─────┘  └───────┬──────────┘ │
└───────┼──────────────┼───────────────┼──────────────┘
        │              │               │
        ▼              ▼               ▼
┌─────────────────────────────────────────────────────┐
│        SUPABASE (aesncvmhlgmdnmhwablm)              │
│  ┌─────────┐  ┌──────────┐  ┌────────────────────┐│
│  │Auth      │  │Database  │  │Edge Functions     ││
│  │(Google,  │  │          │  │ └─ send-email      ││
│  │ Apple)   │  │          │  │                    ││
│  └─────────┘  └──────────┘  └───────┬────────────┘│
└──────────────────────────────────────┼──────────────┘
                                       │
                                       ▼
                               ┌────────────────┐
                               │ Resend API     │
                               └────────────────┘

        ┌──────────────────────────────────────────┐
        │ VERCEL (Hosting)                          │
        │  └─ fintra-admin-deploy.vercel.app       │
        │  └─ fintrahq.com (custom domain)         │
        └──────────────────────────────────────────┘
```

---

## 🔗 Percy Ecosystem

```
┌──────────────────────────────────────────────────────┐
│                  LANDLORD (Flutter)                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────┐ │
│  │Dashboard │ │Room Mgmt │ │ Billing  │ │QR Gen  │ │
│  └─────┬────┘ └────┬─────┘ └────┬─────┘ └───┬────┘ │
└────────┼───────────┼───────────┼────────────┘       │
         │           │           │                     │
         ▼           ▼           ▼                     │
┌──────────────────────────────────────────────────────┐
│        SUPABASE (vxomboffddzpgrfhdwpd)               │
│  ┌────────┐ ┌──────────────────────┐ ┌──────────┐  │
│  │Auth    │ │Edge Functions (6)    │ │Realtime  │  │
│  │(OTP)   │ │create-stay,         │ │(rooms    │  │
│  │        │ │get-room-name/details│ │ stream)  │  │
│  │        │ │notify-checkout,    │ │          │  │
│  │        │ │get-tenant-id-photo │ │          │  │
│  │        │ │summarise-feedback  │ │          │  │
│  └────────┘ └──────────────────────┘ └──────────┘  │
│  ┌──────────────────────────────────────────────────┐│
│  │Postgres (34+ migrations)                        ││
│  │rooms, stays, bills, payments, damage_reports,  ││
│  │rentable_items, consumables, checkout_requests   ││
│  └──────────────────────────────────────────────────┘│
└──────────────────────────────────────────────────────┘
         │           │
         ▼           ▼
┌──────────────────────────────────────────────────────┐
│              TENANT (PWA — Next.js)                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐            │
│  │Check-In  │ │Dashboard │ │Checkout  │            │
│  │(6 steps) │ │(stay mgr)│ │(5 steps) │            │
│  └──────────┘ └──────────┘ └──────────┘            │
│  tenantpwa.vercel.app                                │
└──────────────────────────────────────────────────────┘
```

---

## 🔗 AutoResearch

```
┌──────────────────────────────────────┐
│           program.md                 │
│     (Human-edited instructions)      │
└──────────────┬───────────────────────┘
               │
               ▼
┌──────────────────────────────────────┐
│           AI AGENT                    │
│  Modifies train.py → runs 5-min      │
│  experiment → measures val_bpb        │
└──────────────┬───────────────────────┘
               │
               ▼
┌──────────────────────────────────────┐
│     ~50M param GPT                   │
│  MuonAdamW optimizer                 │
│  Flash Attention 3, RoPE, ReLU²     │
└──────────────┬───────────────────────┘
               │
               ▼
┌──────────────────────────────────────┐
│     results.tsv                       │
│  Keep improvements, revert regressions│
└──────────────────────────────────────┘
```

---

## 📊 Database Tables

### FinTra (Supabase `aesncvmhlgmdnmhwablm`)

| Table | Purpose |
|-------|---------|
| `app_settings` | Admin config (product_name, app_link, from_email, from_name) |
| `email_templates` | HTML email template storage |
| `waitlist` | Beta signup emails + scores |

### Percy (Supabase `vxomboffddzpgrfhdwpd`)

| Table | Purpose |
|-------|---------|
| `rooms` | Room info, rent, status, capacity |
| `stays` | Tenant stays, dates, checkout status |
| `bills` + `bill_items` | Itemized billing |
| `payments` | Cash/UPI/bank tracking |
| `damage_reports` | Damage + complaints |
| `rentable_items` | Add-ons with daily rate |
| `checkout_requests` | Checkout handshake |
| `tenant_consumables` | Water, etc. |
| `push_tokens` | FCM landlord notifications |
| `profiles` | User info (landlord/tenant) |

---

## 📋 Related

- [[Supabase — FinTra Project]]
- [[Percy — Supabase Backend]]
- [[Resend — Email API]]
- [[Vercel — FinTra Admin]]
- [[Vercel — FinTra Landing]]
- [[AutoResearch Architecture]]
- [[Percy System Architecture]]