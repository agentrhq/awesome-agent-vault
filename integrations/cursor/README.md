---
name: Cursor
slug: cursor
type: integration
license: proprietary
stars: n/a
last_verified: 2026-05-27
maintainer: cursor
related: [hook-based-injection]
---

# Cursor

Cursor's MCP configuration accepts environment-variable interpolation through `${env:VAR}` in `~/.cursor/mcp.json`. Interpolation works for stdio MCP servers; the same syntax is broken in HTTP headers for remote MCP servers, which is a footgun rather than a feature.

## Default mechanism

- `~/.cursor/mcp.json` with `${env:VAR}` interpolation in `command`, `args`, and `env`.
- `.cursorrules` for prompt rules; no secret syntax.

## Injection surface

- Per-server `env` map in `mcp.json`.
- OAuth 2.1 plus Dynamic Client Registration for remote MCP.

## Known issue

Interpolation in HTTP headers for remote MCP servers does not work. Users who do not check the forum bug end up pasting raw tokens into `headers`. [Forum thread.](https://forum.cursor.com/t/config-interpolation-env-name-not-working-in-headers-for-remote-mcp-servers/156069)

## Best community example

Infisical's [Cursor Cloud Agents secrets post](https://infisical.com/blog/secure-secrets-management-for-cursor-cloud-agents) uses a sidecar that pulls secrets at runtime.

## Docs

- [TrueFoundry: MCP authentication in Cursor](https://www.truefoundry.com/blog/mcp-authentication-in-cursor-oauth-api-keys-and-secure-configuration)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
