---
name: Mastra
slug: mastra
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-27
maintainer: mastra-ai
related: [scoped-delegation-tokens]
---

# Mastra

Mastra is the only framework on this list that ships a first-party CLI command to sync env from a linked cloud project with restrictive file permissions.

## Default mechanism

- `process.env.*` auto-detected by the model router.
- `MASTRA_JWT_SECRET` for the framework's own auth.

## Injection surface

- `mastra server env import` pulls env from a linked project into `.env` with mode 0600.
- Pluggable auth providers: JWT, Clerk, Supabase, Firebase, WorkOS, Auth0.

## Best community example

The [Agent Authentication System template](https://mastra.ai/templates/agent-authentication-system) wires Clerk through Mastra's auth provider for per-user-scoped credential fetching.

## Docs

- [Configuration reference](https://mastra.ai/reference/configuration)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
