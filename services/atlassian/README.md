---
name: Atlassian
slug: atlassian
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: atlassian
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Atlassian

Atlassian Cloud exposes Jira, Confluence, and related products through a unified REST surface. Authorization uses OAuth 2.0 3-legged (3LO) apps, where an agent receives a scoped access token bound to a specific user and a specific Atlassian site (cloudid). Tokens are minted per consent and carry the granular scopes the user approved.

## Credential types

- OAuth 2.0 3LO access tokens (user-delegated, per cloudid)
- OAuth 2.0 refresh tokens (offline_access scope)
- API tokens (user-level, long-lived, basic auth pairing)
- Forge / Connect app tokens (app-context, not for general agents)

## Recommended pattern

Use OAuth 2.0 3LO with the minimum set of granular scopes (for example, `read:jira-work`, `write:jira-work`, `read:confluence-content.summary`) plus `offline_access`. Bind tokens to a single cloudid and store the refresh token in the vault. Avoid static API tokens for agent use, since they cannot be scoped and inherit the full user permission set.

## Critical scopes to refuse

`manage:jira-configuration`, `manage:jira-project`, `manage:jira-webhook`, `delete:*` scopes on Jira or Confluence, `admin:*` scopes, and any classic (non-granular) scope such as `read:jira-user` paired with broad write access.

## Rotation

3LO access tokens expire after 1 hour and must be refreshed via the refresh token. Refresh tokens are rotating: each refresh returns a new refresh token and invalidates the previous one. Idle refresh tokens expire after 90 days.

## Docs

- [Official docs](https://developer.atlassian.com/cloud/jira/platform/oauth-2-3lo-apps/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
