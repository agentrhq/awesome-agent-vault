---
name: Windsurf
slug: windsurf
type: integration
license: proprietary
stars: n/a
last_verified: 2026-05-27
maintainer: codeium
related: [hook-based-injection]
---

# Windsurf

Windsurf's Cascade reads MCP config from `~/.codeium/windsurf/mcp_config.json` with `${env:VAR}` interpolation across `command`, `args`, `env`, `headers`, and `url`. The shape is similar to Cursor and Claude Code, and the same plaintext-JSON trade-off applies.

## Default mechanism

- `~/.codeium/windsurf/mcp_config.json` with per-server `env` map.
- `${env:VAR}` interpolation in command, args, env, headers, and url.
- `.codeiumignore` excludes secret files from indexing.

## Injection surface

The `env` map per server is the only documented seam. Plaintext JSON by default.

## Best community example

[Cequence AI Gateway Windsurf setup](https://docs.aigateway.cequence.ai/docs/client-config/windsurf/) routes MCP traffic through an auth gateway, which keeps credentials out of `mcp_config.json` entirely.

## Docs

- [Cascade MCP](https://docs.windsurf.com/windsurf/cascade/mcp)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
