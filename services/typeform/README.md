---
name: Typeform
slug: typeform
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: typeform
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Typeform

Typeform exposes a REST API for managing forms, retrieving responses, and reading account data. Authentication is offered through OAuth 2.0 with granular scopes, or via Personal Access Tokens scoped to a single user account. Token selection determines whether agent actions are auditable per user or appear as the workspace owner.

## Credential types

- OAuth 2.0 authorization code flow with explicit scope grants (forms, responses, accounts, webhooks, workspaces, themes, images).
- Personal Access Tokens (PATs) for individual developer or single-user automation.
- Webhook signing secrets for verifying inbound delivery payloads.

## Recommended pattern

For agents acting on behalf of end users, OAuth 2.0 with the narrowest scopes required for the task. Prefer `forms:read` and `responses:read` for analytics workloads. Avoid PATs in shared agent contexts because they carry the full permission set of the issuing user and cannot be scope-limited.

## Critical scopes to refuse

- `accounts:write`, `forms:write` (unless explicitly authoring or modifying forms)
- `webhooks:write`, `workspaces:write`
- `images:write`, `themes:write`
- Any `*:write` scope on a read-only analytical task

## Rotation

OAuth access tokens expire and are refreshed via the refresh token grant. PATs do not expire by default and must be rotated manually through the developer portal. Rotate PATs at least every 90 days and revoke immediately on suspected exposure.

## Docs

- [Official docs](https://www.typeform.com/developers/get-started/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
