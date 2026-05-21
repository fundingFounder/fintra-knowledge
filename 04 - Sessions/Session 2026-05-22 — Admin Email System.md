---
type: session
date: 2026-05-22
duration: long
tags: [session, admin, email, resend, edge-function, obsidian]
---

# Session 2026-05-22 — Admin Email System

> Built the complete email system for FinTra admin dashboard + set up Obsidian knowledge vault.

## 🎯 What We Did

### 1. Email Template Visualizer
- Added **device-frame email visualizer** (Desktop/Tablet/Phone)
- Full email client mockup: From, Subject, Date, "to me" header
- Toggle between Edit mode and Visualize mode
- Real iframe HTML rendering

### 2. HTML Email Sending (Replaced mailto)
- **Replaced plain-text mailto** with **Resend API** via Supabase Edge Function
- "Send All" / "Send Selected" buttons on Waitlist page
- Confirmation dialog with BCC note
- Beautiful HTML emails with FinTra dark theme branding
- Fallback "Open in Client" button for manual sending

### 3. Supabase Edge Function
- Created `send-email` function at `supabase/functions/send-email/index.ts`
- Accepts: recipients array, subject, html body, from_name, from_email
- Sends via Resend API with BCC for privacy
- **Deployed** and **live**
- `RESEND_API_KEY` already existed in Supabase secrets

### 4. Database Migrations
- `app_settings` table: added `from_email` and `from_name` columns
- `email_templates` table: created with RLS policies
- All run via `supabase db query --linked`

### 5. Email Template Settings
- Added **Sender Name** and **Sender Email** fields
- Default: `onboarding@resend.dev` (sends only to Resend account owner)
- Template variables: `{{product_name}}`, `{{app_link}}`

### 6. Obsidian Knowledge Vault
- Created full vault at `~/Documents/Obsidian Vault`
- Organized into: Dashboard, Projects, Architecture, Decisions, Sessions, People, Knowledge, Templates
- Every note cross-linked with `[[]]` wikilinks
- Ready to push to GitHub for web access

---

## 🏗 Decisions Made

- [[ADR-001 — Resend for Email Delivery]]
- [[ADR-002 — Supabase Edge Functions for Backend Logic]]

---

## 🐛 Issues Encountered

| Issue | Fix |
|-------|-----|
| `FunctionResponse.toJson` doesn't exist | Changed to `response.data` |
| `Iterable<Widget>.add()` not valid in Dart | Used spread `...[]` syntax |
| `Icons.mark_email_rounded` doesn't exist | Changed to `Icons.mark_email_unread_outlined` |
| Vercel SSO blocks `.vercel.app` access | Deploy under personal scope `thedarkhorse17` |
| `app_settings` missing `from_email` column | ALTER TABLE migration run via CLI |

---

## 📋 Related

- [[FinTra - Admin Dashboard]]
- [[Resend — Email API]]
- [[Supabase — FinTra Project]]
- [[System Architecture]]