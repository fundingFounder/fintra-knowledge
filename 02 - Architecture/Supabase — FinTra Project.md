---
type: infrastructure
service: Supabase
project_id: aesncvmhlgmdnmhwablm
region: South Asia (Mumbai)
tags: [supabase, backend, database, auth, edge-functions]
---

# Supabase — FinTra Project

> Backend for all FinTra services.

## 🔗 Connections

- **Admin Dashboard:** [[FinTra - Admin Dashboard]]
- **Mobile App:** [[FinTra - Product Overview]]
- **Landing Page:** [[FinTra - Landing Page]]
- **Email:** [[Resend — Email API]]

---

## 🗄 Database

**Project ID:** `aesncvmhlgmdnmhwablm`
**URL:** `https://aesncvmhlgmdnmhwablm.supabase.co`
**Region:** South Asia (Mumbai)

### Secrets (already configured)

| Secret | Purpose |
|--------|---------|
| `RESEND_API_KEY` | Resend email API |
| `ELEVENLABS_API_KEY` | Text-to-speech |
| `GEMINI_API_KEY` | AI features |
| `GROQ_API_KEY` | Fast inference |
| `SERPAPI_KEY` | Web search |
| `PEXELS_API_KEY` | Stock images |
| `OCR_SPACE_API_KEY` | OCR processing |
| `FCM_SERVICE_ACCOUNT_JSON` | Push notifications |
| `SUPABASE_DB_URL` | Direct DB connection |

### Key Tables

- `app_settings` — Config (product_name, app_link, from_email, from_name)
- `email_templates` — HTML email template storage
- `waitlist` — Beta signup emails + scores
- `users` / `expenses` / `future_planning` — App data

---

## ⚡ Edge Functions

| Function | Purpose | Status |
|----------|---------|--------|
| `send-email` | Send HTML emails via Resend | ✅ Deployed |

---

## 📋 Related

- [[ADR-002 — Supabase Edge Functions for Backend Logic]]
- [[System Architecture]]