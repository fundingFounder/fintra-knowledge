---
type: knowledge
category: infrastructure
tags: [supabase, edge-functions, deno, serverless]
---

# Supabase Edge Functions

> Deno-based serverless functions running in Supabase infrastructure.

## 🔗 Connections

- **Used in:** [[FinTra - Admin Dashboard]] for email sending
- **Decision:** [[ADR-002 — Supabase Edge Functions for Backend Logic]]

---

## 📐 How They Work

1. Write TypeScript in `supabase/functions/<name>/index.ts`
2. Use Deno APIs (fetch, env, etc.)
3. Deploy: `supabase functions deploy <name>`
4. Call from client: `supabase.functions.invoke('<name>', body: {...})`
5. Secrets: `supabase secrets set KEY=value`

## 📐 Structure

```typescript
// supabase/functions/send-email/index.ts
import "jsr:@supabase/functions-js/edge-runtime.d.ts";

Deno.serve(async (req) => {
  const { recipients, subject, html, from_name, from_email } = await req.json();
  const RESEND_API_KEY = Deno.env.get("RESEND_API_KEY");
  // ... send via Resend API
});
```

## 📋 Deployed Functions

| Function | Purpose | Status |
|----------|---------|--------|
| `send-email` | Send HTML emails via Resend | ✅ Live |

---

## 📋 Related

- [[Supabase — FinTra Project]]
- [[Resend — Email API]]