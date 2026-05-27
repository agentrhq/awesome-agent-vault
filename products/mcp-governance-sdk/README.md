---
name: mcp-governance-sdk
slug: mcp-governance-sdk
type: product
license: unknown
stars: 38
last_verified: 2026-05-27
maintainer: ithena-one
related: [audit-trails-siem, non-human-identity]
---

# mcp-governance-sdk

Enterprise governance layer for MCP servers. Adds identity, RBAC, credential brokering, and auditing to the MCP SDK so enterprise teams can deploy MCP servers under existing policy frameworks.

## Architecture

Drops in alongside the official MCP SDK. Each tool call passes through identity, policy, credential, and audit middleware before reaching the underlying handler.

## Who it is for

Enterprises rolling MCP servers internally who need IAM hooks rather than ad-hoc env vars.

## Trade-offs

Tied to the MCP SDK's evolution. Worth watching but small community at time of writing.

## Links

- Repo: [github.com/ithena-one/mcp-governance-sdk](https://github.com/ithena-one/mcp-governance-sdk)
- Last updated: 2026-05-25
- Stars: 38

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
