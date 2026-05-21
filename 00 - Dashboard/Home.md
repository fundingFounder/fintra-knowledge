---
type: dashboard
updated: 2026-05-22
tags: [dashboard, mOC]
---

# 🧠 FinTra Knowledge Graph

> *"What we did, what's planned, how it's connected."*

---

## 🗺 Quick Nav

| Area | Key Note |
|------|----------|
| **Projects** | [[FinTra - Project Overview]] |
| **Architecture** | [[System Architecture]] |
| **Decisions** | [[Decision Log]] |
| **Sessions** | [[Session 2026-05-22 — Admin Email System]] |
| **People** | [[Dibyendu Mondal]] |
| **Knowledge** | [[Supabase Edge Functions]] |

---

## 🔥 Active Projects

```dataview
LIST FROM "01 - Projects"
WHERE status = "active"
SORT file.mtime DESC
```

- [[FinTra - Admin Dashboard]] — Flutter web admin panel (deployed, live)
- [[FinTra - Product Overview]] — Mobile finance app (beta)
- [[FinTra - Landing Page]] — fintrahq.com (deployed)

---

## 📊 Recent Decisions

- [[ADR-001 — Resend for Email Delivery]]
- [[ADR-002 — Supabase Edge Functions for Backend Logic]]
- [[ADR-003 — Flutter Web for Admin Dashboard]]

---

## 🕐 Recent Sessions

```dataview
LIST FROM "04 - Sessions"
SORT file.name DESC
LIMIT 5
```

---

## 🔗 Graph Stats

- **Projects:** 3
- **Decisions:** 3
- **Sessions:** 1
- **Knowledge:** 4

---

*This vault is auto-maintained by Hermes Agent. Every chat creates a session note. Every decision gets an ADR. Everything links back.*