---
type: decision
status: accepted
date: 2026-05-22
tags: [adr, email, resend, infrastructure]
---

# ADR-001 — Resend for Email Delivery

## Context

The admin dashboard needs to send beautiful HTML emails to waitlist users. Options considered:

1. **Resend** — Modern email API, free tier (100/day), simple REST API
2. **SendGrid** — Established, 100/day free, more complex setup
3. **Mailgun** — Good deliverability, complex verification
4. **mailto: links** — No API needed, but plain text only, unreliable for bulk
5. **Supabase Auth emails** — Only transactional auth emails, no custom templates

## Decision

**Use Resend** as the email delivery API.

## Rationale

- Simplest REST API — one POST request sends an email
- Free tier (100 emails/day) sufficient for beta waitlist
- Beautiful HTML support out of the box
- Already has API key configured in Supabase secrets
- Called via Supabase Edge Function to keep API key secure server-side

## Consequences

- Default sender `onboarding@resend.dev` only delivers to account owner's email
- For production, must verify a custom domain in Resend
- Rate limited to 100 emails/day on free tier

---

## 📋 Related

- [[Resend — Email API]]
- [[FinTra - Admin Dashboard]]
- [[ADR-002 — Supabase Edge Functions for Backend Logic]]