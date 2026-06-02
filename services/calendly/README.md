---
name: Calendly
slug: calendly
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: calendly
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Calendly

Calendly exposes a scheduling API for users and organizations. Authentication is built on OAuth 2.0 with per-resource scopes, plus Personal Access Tokens as a manual fallback for single-user scripts. Tokens carry organization context, so scope hygiene matters as much as token storage.

## Credential types

- OAuth 2.0 authorization code grant with refresh tokens.
- Personal Access Tokens (PATs), issued from a user's integrations page.
- Webhook signing keys, used to verify event payloads, not to authorize requests.

## Recommended pattern

For an AI agent, prefer OAuth 2.0 with the narrowest scope set the workflow needs and short-lived access tokens refreshed on demand. PATs should be reserved for human-supervised scripts. Scope per resource and store refresh tokens in a vault, never in agent memory or prompts.

## Critical scopes to refuse

Organization-wide admin scopes, webhook subscription management for an entire organization, and routing form write access. An agent that only reads a user's upcoming events does not need scheduled event cancellation or invitee no-show write permissions.

## Rotation

OAuth access tokens are short-lived and refresh automatically via the refresh token. PATs do not rotate automatically. Rotate PATs on a fixed cadence and immediately when a user leaves or a workflow changes.

## Docs

- [Official docs](https://developer.calendly.com/api-docs/ZG9jOjI3NjE3Mjg-authentication)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
