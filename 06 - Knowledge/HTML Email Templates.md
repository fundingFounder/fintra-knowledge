---
type: knowledge
category: email
tags: [email, html, resend, templates]
---

# HTML Email Templates

> Best practices and patterns for beautiful HTML emails.

## 🔗 Connections

- **Used in:** [[FinTra - Admin Dashboard]] → Email Templates page
- **Provider:** [[Resend — Email API]]

---

## 📐 Email Template Structure

```
┌──────────────────────────────────┐
│  Logo + Product Name     🚀     │
├──────────────────────────────────┤
│                                  │
│  🎉 You're In!                   │
│                                  │
│  Thank you for choosing to be    │
│  a part of {{product_name}} beta │
│                                  │
│  ┌──────────────────────┐       │
│  │  Install {{product_name}}   │       │
│  └──────────────────────┘       │
│                                  │
│  💡 We Value Your Feedback      │
│  Please let us know how we      │
│  can improve!                    │
│                                  │
├──────────────────────────────────┤
│  © 2025 {{product_name}} Beta   │
└──────────────────────────────────┘
```

## ⚠️ Email HTML Constraints

- Must use **tables for layout** (not flexbox/grid)
- Inline styles only (no `<style>` blocks — Gmail strips them)
- Use `background:` CSS, not `background-color:`
- All images must be absolute URLs
- Font stack: `'Segoe UI', Arial, sans-serif`
- Max width: 560px
- Mobile: use `%` widths, not fixed px

---

## 📋 Related

- [[FinTra - Admin Dashboard]]
- [[ADR-001 — Resend for Email Delivery]]