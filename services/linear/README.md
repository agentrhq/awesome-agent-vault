---
name: Linear
slug: linear
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: linear
related: [scoped-delegation-tokens]
---

# Linear

Linear supports OAuth 2.0 with actor authorization, which is the right shape for agents: writes are attributed to the agent identity and can be revoked per user without revoking the integration globally.

## Credential types

- **OAuth 2.0 with `actor=app`**: per-user grant. Writes attributed to the agent. Revocable per user.
- **OAuth 2.0 with `actor=user`**: writes attributed to the user. Useful when the agent acts truly on the user's behalf.
- **Personal API keys**: full account access. Use only for trusted server-to-server.

## Recommended pattern

Build a Linear OAuth app, request the narrowest scope set, and store refresh tokens in a vault. Choose `actor=app` so the audit log distinguishes agent actions from human actions.

## Critical scopes to refuse

`admin`, broad `write` on Issues and Projects when `read` is enough, `comments:create` if the agent only reads.

## Rotation

Standard OAuth refresh cadence (provider-defined). Rotate personal keys on owner change.

## Example

```bash
curl -H "Authorization: Bearer $LINEAR_ACCESS_TOKEN" \
  https://api.linear.app/graphql \
  -d '{"query":"{ viewer { id name } }"}'
```

## Docs

- [Linear developers](https://linear.app/developers)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
