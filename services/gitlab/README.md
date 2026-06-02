---
name: GitLab
slug: gitlab
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: gitlab
related: [scoped-delegation-tokens, short-lived-tokens]
---

# GitLab

GitLab exposes its REST and GraphQL APIs through several token families that differ in ownership scope. The credential model is hierarchical. Personal access tokens carry user-level rights, group and project access tokens are bound to a single namespace, and the OAuth2 authorization code flow issues delegated tokens on behalf of a signed-in user.

## Credential types

- Personal access tokens (PATs), user-scoped, configurable expiry and scopes.
- Project access tokens, bound to a single project, behave as a bot user.
- Group access tokens, bound to a group and its subgroups.
- OAuth2 access tokens via the authorization code or PKCE flow, refresh tokens supported.
- CI/CD job tokens, short-lived, injected into pipeline jobs.
- Deploy tokens and deploy keys for repository or registry pull/push.

## Recommended pattern

For an AI agent acting against a single repository, a project access token with the minimum scope (`read_api` or `read_repository`) and an expiry under 90 days is the narrowest practical credential. For agents acting on behalf of an end user, prefer the OAuth2 PKCE flow with a refresh token and a short access-token lifetime.

## Critical scopes to refuse

`api`, `sudo`, `admin_mode`, `write_repository` on protected branches, `write_registry`, `manage_runner`, and any group-owner role.

## Rotation

GitLab requires expiry dates on PATs and project tokens, with a maximum lifetime enforced by instance policy. Rotate via the `POST /personal_access_tokens/self/rotate` endpoint or by issuing a new token and revoking the old one through the UI or API.

## Docs

- [Official docs](https://docs.gitlab.com/ee/api/oauth2.html)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
