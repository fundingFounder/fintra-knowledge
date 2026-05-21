---
type: decision
status: accepted
date: 2026-05-21
tags: [adr, flutter, web, admin]
---

# ADR-003 — Flutter Web for Admin Dashboard

## Context

Need an admin dashboard to manage FinTra beta users, waitlist, and send email campaigns. Options:

1. **Flutter Web** — Same codebase as mobile, single codebase
2. **React Admin** — Web-optimized, larger ecosystem
3. **Next.js** — Full-stack, SSR, heavy setup
4. **Retool** — Low-code, fast but limited customization

## Decision

**Use Flutter Web** for the admin dashboard.

## Rationale

- Same language (Dart) as the FinTra mobile app — team knowledge
- Single `flutter build web --release` for deployment
- Native mobile-responsive design (sidebar→bottom nav at 768px)
- Beautiful dark theme consistent with FinTra brand
- Vercel deployment works with clean temp dir approach

## Consequences

- Flutter Web has larger initial bundle size than React
- Must deploy from temp dir (not project root) due to 750MB+ project size
- Vercel SSO protection requires personal scope deployment
- Some web-specific workarounds needed (HtmlElementView for iframe, etc.)

---

## 📋 Related

- [[FinTra - Admin Dashboard]]
- [[Vercel — FinTra Admin]]