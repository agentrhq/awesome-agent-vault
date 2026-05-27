---
name: Vercel AI SDK
slug: vercel-ai-sdk
type: integration
license: Apache-2.0
stars: n/a
last_verified: 2026-05-27
maintainer: vercel
related: [scoped-delegation-tokens]
---

# Vercel AI SDK

The cleanest cloud credential story on this list, when the agent runs on Vercel. Sensitive env vars are write-only, and the AI Gateway accepts an OIDC token instead of a long-lived key.

## Default mechanism

- `process.env` inside `tool({ execute })`.
- Vercel-managed env vars with a "Sensitive" (write-only) flag.
- `AI_GATEWAY_API_KEY` or OIDC token for the gateway.

## Injection surface

- `vercel env pull` to fetch env into `.env.local` for local development.
- OIDC federation via `x-vercel-oidc-token` for production calls to the gateway.

## Best community example

[Speakeasy's Gram pattern](https://www.speakeasy.com/docs/gram/examples/using-environments-with-vercel-ai-sdk) uses environments with the Vercel AI SDK so each tool call carries the right environment's credentials.

## Docs

- [Authentication and BYOK](https://vercel.com/docs/ai-gateway/authentication-and-byok)
- [Sensitive environment variables](https://vercel.com/docs/environment-variables/sensitive-environment-variables)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
