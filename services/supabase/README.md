---
name: Supabase
slug: supabase
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: supabase
related: [per-task-scoping, scoped-delegation-tokens]
---

# Supabase

Supabase is a worked cautionary example for agents. The legacy `service_role` JWT bypasses Row Level Security, and the 2025 Cursor incident showed what happens when an agent ingests untrusted text while holding it. Use the new key types and never give an agent a service-role JWT.

## Credential types

- **Publishable key** (`sb_publishable_`): client-side, RLS-respecting.
- **Secret key** (`sb_secret_`): server-side, full access. Replaces legacy service_role.
- **Legacy `anon` JWT**: client-side, RLS-respecting. Being phased out.
- **Legacy `service_role` JWT**: bypasses RLS. Being phased out. Never expose to an agent.

## Recommended pattern

Server-side agents use a secret key behind a thin API that performs only the operations the agent should be able to perform. The agent itself never holds the secret key; it calls the API.

## Critical scopes to refuse

`service_role` JWT or secret-key usage from any edge code, any direct `auth.admin` calls, MCP servers that hold service-role credentials.

## Rotation

Rotate via dashboard. Deletion is immediate and breaks any client still using the key. Migrate off legacy JWT keys.

## Example

```bash
# Read with RLS enforced (publishable key)
curl -H "apikey: sb_publishable_..." \
  -H "Authorization: Bearer sb_publishable_..." \
  https://xxx.supabase.co/rest/v1/posts
```

## Docs

- [API keys](https://supabase.com/docs/guides/api/api-keys)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
