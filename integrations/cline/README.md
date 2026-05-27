---
name: Cline
slug: cline
type: integration
license: Apache-2.0
stars: n/a
last_verified: 2026-05-27
maintainer: cline
related: []
---

# Cline

VS Code coding agent. The credential surface is minimal: provider keys configured in the extension settings, MCP server config for third-party tools.

## Default mechanism

- VS Code extension settings for model provider keys.
- MCP server config (similar shape to Claude Code) for external tools.
- Environment variables read by spawned shells.

## Injection surface

MCP servers can carry their own credential conventions. There is no first-party broker or hook surface beyond env vars.

## Notes

Wrap Cline in a credential proxy (Authsome, Infisical Agent Vault, onecli) for any agent setup that needs more than direct env-var configuration.

## Docs

- Repo: [github.com/cline/cline](https://github.com/cline/cline)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
