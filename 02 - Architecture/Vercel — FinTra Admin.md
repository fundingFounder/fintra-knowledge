---
type: infrastructure
service: Vercel
tags: [vercel, hosting, deployment]
---

# Vercel — FinTra Admin

> Hosting for the FinTra admin dashboard Flutter web app.

## 📊 Deployment Details

| | |
|---|---|
| **Project** | `fintra-admin-deploy` |
| **URL** | https://fintra-admin-deploy.vercel.app |
| **Scope** | Personal (`thedarkhorse17`) |
| **Org** | `thedarkhorse17s-projects` |

---

## ⚠️ SSO Note

The Vercel team `thedarkhorse17s-projects` has **SAML SSO protection enabled** — all `.vercel.app` URLs redirect to login. The admin dashboard is deployed under **personal scope** to bypass this and work on phones without login.

---

## 🚀 Deploy Process

```bash
# Build
cd /Users/dibyendumondal/Unicorns/FinTra/FinTra_admin/fintra_admin
flutter build web --release

# Sync to clean temp dir (project root is 750MB+)
rm -rf /tmp/fintra-admin-deploy
mkdir -p /tmp/fintra-admin-deploy
cp -r build/web/* /tmp/fintra-admin-deploy/

# Deploy
cd /tmp/fintra-admin-deploy && rm -rf .vercel && vercel deploy --prod -y
```

**Critical:** Must deploy from `/tmp/fintra-admin-deploy/`, NOT project root (750MB+ would exceed Vercel limits).

---

## 📋 Related

- [[Vercel — FinTra Landing]]
- [[FinTra - Admin Dashboard]]
- [[ADR-003 — Flutter Web for Admin Dashboard]]