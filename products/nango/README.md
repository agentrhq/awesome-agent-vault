---
name: Nango
slug: nango
type: product
license: unknown
stars: 9698
last_verified: 2026-05-28
maintainer: NangoHQ
related: ["scoped-delegation-tokens"]
---

# Nango

Nango is an OAuth-token broker positioned for agents and MCP workloads. It manages the authorization lifecycle for hundreds of third-party APIs, handling consent flows, token storage, refresh, and revocation. Agents request scoped access on demand rather than holding long-lived credentials in process memory, which keeps API keys and refresh tokens off the agent runtime and inside a dedicated service boundary.

## Architecture

Nango runs as a separate service that fronts third-party providers. Developers configure integrations once, and end users authenticate through Nango's hosted or self-hosted OAuth flows. Tokens are stored server-side and indexed by a connection identifier. The agent or MCP server calls Nango with the connection id and receives either a short-lived access token or a proxied response. Refresh, rotation, and provider-specific quirks (PKCE, custom headers, signed requests) are handled inside Nango, not by the calling code.

## Who it is for

Teams shipping agents or MCP servers that need to talk to many SaaS APIs on behalf of users. It fits products where each end user brings their own account at Slack, HubSpot, Notion, Linear, and similar tools, and where storing per-user refresh tokens in the agent process is not acceptable.

## Trade-offs

Nango is a token broker, not a general secret manager. It does not cover static API keys, database credentials, or signing keys, and self-hosting introduces a stateful service with its own database and uptime requirements. Provider coverage is broad but uneven · less common APIs may need custom integration definitions before they work.

## Links

- Repo: [github.com/NangoHQ/nango](https://github.com/NangoHQ/nango)
- Stars: 9698
- License: unknown

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
