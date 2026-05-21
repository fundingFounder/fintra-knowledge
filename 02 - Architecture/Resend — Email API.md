---
type: infrastructure
service: Resend
tier: free (100 emails/day)
tags: [resend, email, api, infrastructure]
---

# Resend — Email API

> Email delivery service for sending beautiful HTML emails from the admin dashboard.

## 🔗 Connections

- **Used by:** [[Supabase — FinTra Project]] (via edge function `send-email`)
- **Triggered from:** [[FinTra - Admin Dashboard]] → Waitlist page
- **Template editor:** [[FinTra - Admin Dashboard]] → Email Templates page

---

## 📊 Plan

| | |
|---|---|
| **Tier** | Free |
| **Limit** | 100 emails/day |
| **Default Sender** | `onboarding@resend.dev` |
| **Limitation** | On free tier, `onboarding@resend.dev` only sends to the account owner's email |

## ⚠️ Production Setup

To send to **any** email address:
1. Go to [resend.com](https://resend.com) → Domains
2. Add & verify your domain (e.g. `fintrahq.com`)
3. Update **Sender Email** in Admin → Email Templates → Settings
4. Update DNS records as Resend instructs

---

## 🔧 How It Works

```
Admin Dashboard → Waitlist "Send All/Selected"
    → Supabase Edge Function (send-email)
        → Resend API (https://api.resend.com/emails)
            → HTML email delivered to recipients
```

- Emails are **BCC'd** — recipients don't see each other
- Template loaded from `email_templates` table in Supabase
- Variables `{{product_name}}` and `{{app_link}}` auto-replaced

---

## 📋 Related

- [[ADR-001 — Resend for Email Delivery]]
- [[FinTra - Admin Dashboard]]