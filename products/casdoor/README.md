---
name: Casdoor
slug: casdoor
type: product
license: Apache-2.0
stars: 13708
last_verified: 2026-05-28
maintainer: casdoor
related: ["non-human-identity"]
---

# Casdoor

Casdoor is an open-source identity and access management server that has extended its scope to cover AI agents alongside human users. It bundles a traditional auth server supporting OAuth 2.0, OIDC, SAML, CAS, LDAP, and SCIM with a more recent MCP gateway component aimed at brokering LLM tool calls. The project positions itself as a single identity layer for both end users and autonomous agents.

## Architecture

Casdoor runs as a Go backend with a React admin UI, backed by a relational database such as MySQL, PostgreSQL, or SQLite. Applications integrate by registering as OAuth/OIDC clients and redirecting users to the Casdoor login flow. Tokens, sessions, and user records are stored centrally, with adapters for syncing identities via SCIM or LDAP. The MCP gateway sits in front of upstream MCP servers and applies Casdoor-issued credentials and policy before forwarding tool calls from agents.

## Who it is for

Teams that already need a self-hosted IAM server for their product and want one system that also handles agent identity and MCP traffic, rather than running a separate vault or proxy. Common adopters are companies with on-prem or sovereignty requirements who prefer Apache-2.0 over commercial Auth0 or Okta deployments.

## Trade-offs

Casdoor's surface area is wide. Running it well means operating a database, the auth server, the admin UI, and the MCP gateway, plus keeping schema migrations current across releases. Teams that only need agent credential injection for a handful of third-party APIs will find it heavier than a focused vault, and the MCP gateway features are newer than the core IAM.

## Links

- Repo: [github.com/casdoor/casdoor](https://github.com/casdoor/casdoor)
- Stars: 13708
- License: Apache-2.0

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
