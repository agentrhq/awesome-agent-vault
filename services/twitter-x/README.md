---
name: X (Twitter)
slug: twitter-x
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: x
related: [scoped-delegation-tokens, short-lived-tokens]
---

# X (Twitter)

X has migrated authentication to OAuth 2.0 with PKCE, replacing the legacy v1.1 consumer key and access token pairs. Scopes are granular and granted per request: read, write, and direct message access are independent grants. Agents acting on behalf of a user should obtain a delegated token through the authorization code flow with PKCE, never a static API key.

## Credential types

- OAuth 2.0 user context tokens with PKCE (recommended for agents).
- OAuth 2.0 App-Only bearer tokens (read-only, app context).
- Legacy OAuth 1.0a consumer keys and access tokens (v1.1, deprecated for most endpoints).
- API Key and Secret pairs for app registration.

## Recommended pattern

Use OAuth 2.0 with PKCE and request only the minimum scopes needed. Store the refresh token in a vault, exchange for short-lived access tokens at call time, and never expose the API key or secret to the agent runtime.

## Critical scopes to refuse

- `dm.read`, `dm.write` (direct message access).
- `tweet.write`, `tweet.moderate.write` unless posting is the explicit task.
- `users.read` at scale (follower graph extraction).
- `offline.access` should be limited to vault-side refresh, not exposed to agent code.

## Rotation

Access tokens expire after two hours and must be refreshed using the refresh token. Rotate refresh tokens on a 90-day cadence or sooner if scope changes; revoke immediately on suspected leak via the OAuth 2.0 revoke endpoint.

## Docs

- [Official docs](https://docs.x.com/resources/fundamentals/authentication/oauth-2-0/overview)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
