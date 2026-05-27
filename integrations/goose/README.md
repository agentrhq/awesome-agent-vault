---
name: Goose
slug: goose
type: integration
license: Apache-2.0
stars: n/a
last_verified: 2026-05-27
maintainer: block
related: []
---

# Goose

Block's open-source coding agent. Extensions follow an MCP-like shape; credentials flow through extension config and environment variables.

## Default mechanism

- `~/.config/goose/config.yaml` for provider configuration.
- Per-extension env vars.

## Injection surface

Extensions can declare their own credential requirements. The agent process inherits the parent shell's environment by default.

## Notes

Same trade-offs as Cline: no first-party broker. Wrap in a credential proxy for production setups.

## Docs

- Repo: [github.com/block/goose](https://github.com/block/goose)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
