---
name: Klaviyo
slug: klaviyo
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: klaviyo
related: [scoped-delegation-tokens]
---

# Klaviyo

Klaviyo exposes two distinct credential shapes. OAuth 2.0 is used for marketplace and third-party integrations that act on behalf of a Klaviyo account. Private API keys are used for first-party automation inside an account owner's own systems. The two paths use different scopes, different rotation rules, and different revocation surfaces.

## Credential types

- OAuth 2.0 authorization code flow with refresh tokens, scoped per resource (profiles, lists, campaigns, events, metrics).
- Private API keys, created in the Klaviyo UI, scoped read-only or read-write per resource family.
- Public API key (site ID), used only for client-side tracking. Not a secret.

## Recommended pattern

For an agent acting on behalf of a Klaviyo customer, prefer OAuth with the minimum resource scopes required. Refresh tokens should be held by the credential vault, not the agent process. For first-party agent work inside a single account, a private API key restricted to the specific resource family is acceptable, injected at request time and never written to disk.

## Critical scopes to refuse

`accounts:write`, `campaigns:write`, `lists:write` on production lists, `profiles:write` with bulk delete, `templates:write`, and any `*:write` scope on billing or sender identity.

## Rotation

Private API keys do not auto-expire and should be rotated on a fixed cadence, typically every 90 days, via the Klaviyo API keys page. OAuth refresh tokens are revoked through the connected apps screen or by re-running the consent flow.

## Docs

- [Official docs](https://developers.klaviyo.com/en/docs/authenticate-an-account)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
