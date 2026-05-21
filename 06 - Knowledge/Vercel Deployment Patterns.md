---
type: knowledge
category: infrastructure
tags: [vercel, deployment, flutter-web, sso]
---

# Vercel Deployment Patterns

> How to deploy Flutter web apps and other projects to Vercel.

## 🔗 Connections

- **Admin:** [[Vercel — FinTra Admin]]
- **Landing:** [[Vercel — FinTra Landing]]

---

## 📐 Key Lessons

### Flutter Web Deploys MUST Use Temp Dir
Flutter projects are 750MB+ with all dependencies. Deploying from project root exceeds Vercel limits.

```bash
# Correct approach
rm -rf /tmp/fintra-admin-deploy
mkdir -p /tmp/fintra-admin-deploy
cp -r build/web/* /tmp/fintra-admin-deploy/
# Add vercel.json for SPA rewrites
cd /tmp/fintra-admin-deploy && rm -rf .vercel && vercel deploy --prod -y
```

### SSO Protection Bypass
Team `thedarkhorse17s-projects` has SAML SSO. Options:
1. Deploy under personal scope (`--scope thedarkhorse17`) — works but `.vercel.app` URLs still hit SSO
2. Use custom domain — SSO is bypassed for custom domains
3. Disable auth protection per-project in Dashboard → Settings → Authentication

### SPA Rewrites
Flutter web is a single-page app. Must include `vercel.json`:
```json
{
  "rewrites": [
    { "source": "/(.*)", "destination": "/index.html" }
  ]
}
```

---

## 📋 Related

- [[ADR-003 — Flutter Web for Admin Dashboard]]