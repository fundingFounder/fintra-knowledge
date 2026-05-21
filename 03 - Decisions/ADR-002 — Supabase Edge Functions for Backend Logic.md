---
type: decision
status: accepted
date: 2026-05-22
tags: [adr, supabase, edge-functions, backend]
---

# ADR-002 — Supabase Edge Functions for Backend Logic

## Context

The admin dashboard needs to call external APIs (Resend) without exposing API keys to the client. Options:

1. **Supabase Edge Functions** — Deno-based serverless, runs in Supabase infra
2. **Separate backend** — Node.js/Express server deployed separately
3. **Vercel Serverless Functions** — Would need separate Vercel project
4. **Client-side calls** — Exposes API keys, insecure

## Decision

**Use Supabase Edge Functions** for all backend logic that needs secret API keys.

## Rationale

- API keys stay in Supabase secrets — never exposed to client
- Deploys with `supabase functions deploy` — simple workflow
- Already using Supabase as backend — no new infra
- Deno runtime — TypeScript support, CORS handling built-in
- `send-email` edge function working and deployed

## Consequences

- Deno runtime (not Node.js) — some npm packages won't work
- Cold starts on first invocation
- Limited to Supabase's deployed regions

---

## 📋 Related

- [[Supabase — FinTra Project]]
- [[ADR-001 — Resend for Email Delivery]]