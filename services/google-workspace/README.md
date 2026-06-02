---
name: Google Workspace
slug: google-workspace
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: google
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Google Workspace

Google Workspace exposes Gmail, Calendar, Drive, Docs, Sheets, Admin SDK, and other surfaces behind a single OAuth 2.0 system. Each surface has its own scope namespace, and the credential model splits cleanly between user-context tokens and service-account identities used for server-to-server traffic.

## Credential types

- OAuth 2.0 user tokens (access token + refresh token) with per-scope grants.
- Service accounts with JSON key files for server-to-server calls.
- Service accounts with domain-wide delegation, impersonating a Workspace user.
- Workload Identity Federation, mapping external identities to a service account without a static key.
- API keys, limited to a small set of public, unauthenticated endpoints.

## Recommended pattern

For agents acting on behalf of a human, use OAuth 2.0 with the narrowest read-only scope per Workspace surface and a short-lived access token refreshed on demand. For background jobs, prefer Workload Identity Federation over long-lived service account JSON keys, and enable domain-wide delegation only when impersonation is strictly required.

## Critical scopes to refuse

`https://mail.google.com/`, `gmail.modify`, `gmail.send`, `drive` (full), `drive.file` when broader than the task, `admin.directory.user`, `admin.directory.group`, `admin.directory.domain`, `cloud-platform`, any `*.readonly` scope wider than the surface the agent actually touches.

## Rotation

OAuth refresh tokens stay valid until revoked or unused for six months. Service account keys do not expire on their own and must be rotated on a fixed cadence, typically every 90 days, via the IAM API or by switching to Workload Identity Federation to remove the key entirely.

## Docs

- [Official docs](https://developers.google.com/identity/protocols/oauth2)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
