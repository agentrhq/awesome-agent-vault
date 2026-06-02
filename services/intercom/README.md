---
name: Intercom
slug: intercom
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: intercom
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Intercom

Intercom supports two credential models for API access. OAuth 2.0 is used by apps distributed through the Intercom App Store and by integrations acting on behalf of multiple workspaces. Long-lived access tokens are issued to internal apps that act on a single workspace. Both are bearer credentials that authorize against a scoped set of resource families.

## Credential types

- OAuth 2.0 authorization code flow for marketplace and multi-workspace apps
- Long-lived access tokens for internal apps, scoped per app
- Identity Verification HMAC for end-user impersonation safety, not an API credential

## Recommended pattern

For an AI agent acting on one workspace, register an internal app and use its access token. Restrict the app to the resource families the agent actually needs, typically conversations, contacts, or articles. For multi-tenant deployments, use OAuth and store per-workspace tokens behind a broker.

## Critical scopes to refuse

Write access to admins, write access to teams, manage workspace settings, delete conversations, manage app store listings, billing.

## Rotation

Access tokens do not expire by default but can be revoked from the Developer Hub. Rotate on a fixed cadence, for example every 90 days, and on staff offboarding. OAuth refresh is not used; reauthorize the app to mint a new token.

## Docs

- [Official docs](https://developers.intercom.com/docs/build-an-integration/learn-more/authentication/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
