---
type: architecture
updated: 2026-05-22
tags: [architecture, mOC]
---

# System Architecture

> How everything connects in the FinTra ecosystem.

## 🔗 Architecture Diagram

```
┌─────────────────────────────────────────────────────┐
│                    USERS                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────────────┐  │
│  │ Mobile   │  │ Mobile   │  │ Admin (Dibyendu) │  │
│  │ App      │  │ App      │  │ Dashboard        │  │
│  └────┬─────┘  └────┬─────┘  └───────┬──────────┘  │
└───────┼──────────────┼───────────────┼──────────────┘
        │              │               │
        ▼              ▼               ▼
┌─────────────────────────────────────────────────────┐
│              SUPABASE (aesncvmhlgmdnmhwablm)        │
│  ┌─────────┐  ┌──────────┐  ┌────────────────────┐ │
│  │ Auth    │  │ Database │  │ Edge Functions     │ │
│  │         │  │          │  │  └─ send-email     │ │
│  └─────────┘  └──────────┘  └────────┬───────────┘ │
└───────────────────────────────────────┼─────────────┘
                                        │
                                        ▼
                                ┌───────────────┐
                                │ Resend API    │
                                │ (email delivery│
                                │  100/day free) │
                                └───────────────┘
```

## 📊 Database Tables

| Table | Purpose | Key Fields |
|-------|---------|------------|
| `app_settings` | Admin config | product_name, app_link, from_email, from_name |
| `email_templates` | Email template storage | subject, body_html, name |
| `waitlist` | Beta signups | email, score, status |
| `users` | App users | salary, categories, goals |
| `expenses` | Expense tracking | amount, category, date |
| `future_planning` | Monthly projections | month, allocations |

---

## 📋 Related

- [[Supabase — FinTra Project]]
- [[Resend — Email API]]
- [[FinTra - Admin Dashboard]]
- [[FinTra - Product Overview]]