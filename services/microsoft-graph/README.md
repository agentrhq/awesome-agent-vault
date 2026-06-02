---
name: Microsoft Graph
slug: microsoft-graph
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: microsoft
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Microsoft Graph

Microsoft Graph is the unified API surface for Microsoft 365, Entra ID, Intune, and related tenant resources. Authentication is brokered through Entra ID (formerly Azure AD) using OAuth 2.0, with permissions split between application (app-only) and delegated (user-context) modes. Scope granularity is per resource family, e.g. `Mail.Read`, `Files.ReadWrite.All`, `Directory.Read.All`.

## Credential types

- Delegated OAuth 2.0 access tokens (user signs in, agent acts on their behalf)
- Application access tokens (client credentials flow, app-only, no user)
- Certificate-based client credentials (preferred over client secrets)
- Managed identity tokens (when the agent runs inside Azure)
- Client secrets (supported but discouraged)

## Recommended pattern

For an agent calling Graph, use delegated OAuth 2.0 with the narrowest per-resource scopes the task requires, acquired via authorization code + PKCE. Use application permissions only when no user is present, and back them with certificate credentials or a managed identity rather than a client secret.

## Critical scopes to refuse

`Directory.ReadWrite.All`, `Directory.AccessAsUser.All`, `RoleManagement.ReadWrite.Directory`, `Application.ReadWrite.All`, `User.ReadWrite.All`, `Mail.ReadWrite` tenant-wide, `Files.ReadWrite.All`, `full_access_as_app`.

## Rotation

Access tokens are short-lived (typically ~1 hour) and refreshed via refresh tokens or fresh client-credentials calls. Client secrets and certificates should be rotated on a fixed cadence (90 to 180 days) through Entra ID app registration; managed identities rotate automatically.

## Docs

- [Official docs](https://learn.microsoft.com/en-us/graph/auth/auth-concepts)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
