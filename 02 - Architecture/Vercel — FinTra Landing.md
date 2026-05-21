---
type: infrastructure
service: Vercel
tags: [vercel, hosting, deployment]
---

# Vercel — FinTra Landing

> Hosting for the FinTra landing page at fintrahq.com.

## 📊 Deployment Details

| | |
|---|---|
| **Project** | `ultimate-landing` |
| **URL** | https://fintrahq.com |
| **Custom domain** | fintrahq.com (+ www.fintrahq.com) |
| **Framework** | React (CRA + Tailwind) |
| **Root dir** | `frontend/` |
| **Auto-deploy** | Push to `main` triggers deploy |

---

## ⚠️ Notes

- Custom domain bypasses SSO — `fintrahq.com` serves without auth gate
- Non-team-member git commits get BLOCKED (seatBlock: COMMIT_AUTHOR_REQUIRED)
- Use Vercel API authenticated as team member to trigger deploys

---

## 📋 Related

- [[FinTra - Landing Page]]
- [[Vercel — FinTra Admin]]