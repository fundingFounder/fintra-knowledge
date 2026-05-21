---
type: project
status: active
stack: Flutter Web, Supabase, Resend
url: https://fintra-admin-deploy.vercel.app
repo: /Users/dibyendumondal/Unicorns/FinTra/FinTra_admin/fintra_admin/
tags: [fintra, admin, dashboard, flutter, web]
created: 2026-05-21
---

# FinTra - Admin Dashboard

> Flutter web admin panel for managing FinTra beta users, waitlist, finances, and email campaigns.

## 🔗 Connections

- **Backend:** [[Supabase — FinTra Project]]
- **Email Provider:** [[Resend — Email API]]
- **Hosting:** [[Vercel — FinTra Admin]]
- **Product:** [[FinTra - Product Overview]]
- **Landing:** [[FinTra - Landing Page]]

---

## 📐 Architecture

7-page sidebar/bottom-nav Flutter web app:

| Page | Purpose | Key Features |
|------|---------|--------------|
| **Overview** | Dashboard stats | Total users, active streaks, balance summary |
| **Users** | User management | Search, view details, salary/expense breakdown |
| **Finances** | Financial overview | Revenue, transactions, category analysis |
| **Engage** | Engagement tracking | Streaks, category splits, spending patterns |
| **Waitlist** | Waitlist + email | Send HTML emails to waitlist, select all/BCC |
| **Support** | Support tickets | Issue tracking, status management |
| **Email Templates** | Email editor | Visual form editor, live preview, device visualizer |

---

## 📧 Email System

- **Send flow:** Waitlist → Supabase Edge Function `send-email` → Resend API → HTML email
- **Template editor:** Visual form fields (greeting, body, CTA button, feedback) + advanced HTML mode
- **Preview:** Real iframe rendering, Desktop/Tablet/Phone device frames
- **Settings:** Product name, app link, sender name, sender email
- **Storage:** `app_settings` + `email_templates` tables in Supabase

### Current limitation
Default sender `onboarding@resend.dev` only sends to the Resend account owner. For production, verify a custom domain at [resend.com](https://resend.com).

---

## 🚀 Deployment

- **Platform:** Vercel (personal scope `thedarkhorse17`)
- **URL:** https://fintra-admin-deploy.vercel.app
- **Build:** `flutter build web --release`
- **Deploy:** `cd /tmp/fintra-admin-deploy && rm -rf .vercel && vercel deploy --prod -y`
- **Note:** Must deploy from clean temp dir (`/tmp/fintra-admin-deploy/`), not project root (750MB+)

---

## 🛠 Key Files

| File | Purpose |
|------|---------|
| `lib/main.dart` | Supabase init, app config |
| `lib/shell.dart` | 7-page nav (sidebar + bottom) |
| `lib/waitlist_page.dart` | Waitlist + email send UI |
| `lib/email_templates_page.dart` | Visual email editor + preview |
| `lib/theme.dart` | Dark theme, responsive helpers |
| `supabase/functions/send-email/index.ts` | Resend edge function |
| `supabase_migration.sql` | SQL for app_settings + email_templates |

---

## 📋 Related

- [[ADR-001 — Resend for Email Delivery]]
- [[ADR-003 — Flutter Web for Admin Dashboard]]
- [[Session 2026-05-22 — Admin Email System]]