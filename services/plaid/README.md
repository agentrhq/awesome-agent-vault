---
name: Plaid
slug: plaid
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: plaid
related: [scoped-delegation-tokens]
---

# Plaid

Plaid splits credentials into `client_id` + secret (server identity), Link tokens (ephemeral, for the client flow), public tokens (30 minutes, exchanged for access tokens), and per-user Item access tokens (long-lived).

## Credential types

- **`client_id` + secret**: server identity, per environment (Sandbox / Development / Production).
- **Link token**: ephemeral, scoped to one user session.
- **Public token**: 30 minutes, exchanged once for an Item access token.
- **Item access token**: long-lived, one per linked user Item.

## Recommended pattern

One Item access token per linked user. Rotate via `/item/access_token/invalidate` rather than reissuing the user's flow. Sandbox and Production secrets live in separate vaults; never cross environments.

## Critical scopes to refuse

Production secret in a development agent. Reuse of Item tokens across users.

## Rotation

`/item/access_token/invalidate` mints a new access token for the same Item. Rotate per environment on incident.

## Example

```bash
curl https://production.plaid.com/item/access_token/invalidate \
  -H "Content-Type: application/json" \
  -d '{"client_id":"...","secret":"...","access_token":"access-prod-..."}'
```

## Docs

- [Plaid items API](https://plaid.com/docs/api/items/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
