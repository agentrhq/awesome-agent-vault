---
name: mcp-secrets-plugin
slug: mcp-secrets-plugin
type: product
license: unknown
stars: 58
last_verified: 2026-05-27
maintainer: amirshk
related: [hook-based-injection, token-substitution-proxy]
---

# mcp-secrets-plugin

Credential management for MCP servers that leverages the system-native keychain. Designed specifically for the MCP server side of the credential surface rather than the broader agent runtime.

## Architecture

An MCP server registers the plugin; the plugin resolves secret references against the OS keychain at tool-call time. MCP clients (Claude Code, Cursor, Windsurf) never see the plaintext.

## Who it is for

MCP server authors who want a portable way to handle credentials without inventing a custom auth flow per server.

## Trade-offs

MCP-server-scoped. Useful precisely because it stays in its lane; not a general-purpose vault.

## Links

- Repo: [github.com/amirshk/mcp-secrets-plugin](https://github.com/amirshk/mcp-secrets-plugin)
- Last updated: 2026-05-19
- Stars: 58

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
