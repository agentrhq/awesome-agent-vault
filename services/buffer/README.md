---
name: Buffer
slug: buffer
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: buffer
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Buffer

Buffer exposes a social publishing API guarded by OAuth 2.0. Access tokens are issued per user and refresh tokens allow long-lived background access. Scopes are granted per social channel and per operation (publish, read analytics, manage profiles), so a token only carries the channel-operation pairs the user approved at consent time.

## Credential types

- OAuth 2.0 access tokens (short-lived, channel-scoped).
- OAuth 2.0 refresh tokens (long-lived, used to mint new access tokens).
- Legacy personal access tokens (deprecated for new integrations).

## Recommended pattern

For an AI agent, broker OAuth 2.0 through a vault that holds the refresh token and hands the agent a per-task access token limited to the specific channels and operations needed (for example, publish to one connected Twitter profile only). The agent never sees the refresh token.

## Critical scopes to refuse

account-wide write, profile management (connect or disconnect channels), billing or organization admin, bulk delete of scheduled posts, read of full analytics history beyond the current task window.

## Rotation

Refresh tokens should be rotated on a fixed cadence (30 to 90 days) and revoked immediately on suspected agent compromise. Access tokens expire on Buffer's schedule and are refreshed on demand by the vault.

## Docs

- [Official docs](https://buffer.com/developers/api/oauth)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
