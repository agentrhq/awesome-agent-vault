---
name: Zapier
slug: zapier
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: zapier
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Zapier

Zapier exposes two credential surfaces. Embedded integrations and partner apps authenticate end users via OAuth flows, while internal Zaps and team automations rely on long-lived API keys scoped to a Zapier team or account. Zapier Connect handles the OAuth dance on the agent side, returning per-user access tokens that the agent can store and replay.

## Credential types

- OAuth 2.0 access tokens (per end user, issued through Zapier Connect for embedded use cases)
- OAuth 2.0 refresh tokens (long-lived, paired with access tokens)
- Team-scoped API keys (static, used for internal Zaps and admin endpoints)
- Personal API keys (account-level, used for the Platform CLI and developer tooling)

## Recommended pattern

For an AI agent acting on behalf of a user, prefer OAuth access tokens obtained through Zapier Connect over static API keys. Tokens are bound to a specific user and can be revoked individually without disrupting other automations. Reserve team-scoped API keys for back-office agents that operate under a single service identity.

## Critical scopes to refuse

zap:write on production accounts, admin or team-admin scopes, billing access, the ability to install or modify private apps, and any scope granting read access to other users' connected accounts.

## Rotation

OAuth access tokens expire on a short cadence and refresh automatically. API keys do not rotate on their own. Rotate team and personal API keys at least every 90 days through the Zapier developer dashboard, and revoke immediately on suspected exposure.

## Docs

- [Official docs](https://platform.zapier.com/docs/start)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
