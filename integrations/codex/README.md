---
name: Codex CLI
slug: codex
type: integration
license: proprietary
stars: n/a
last_verified: 2026-05-27
maintainer: openai
related: [hook-based-injection, scoped-delegation-tokens]
---

# Codex CLI

OpenAI's CLI coding agent. One of the few platforms in this list with a real OS keyring option out of the box.

## Default mechanism

- `~/.codex/config.toml` plus OS environment variables.
- Per-provider `env_key = "FOO_API_KEY"` declarations.
- Optional OS keyring: `cli_auth_credentials_store = "keyring"`.

## Injection surface

- Custom providers via `[model_providers.*]` blocks in `config.toml`.
- `--with-api-key` accepts a key on stdin (avoids leaving it in shell history).

## Best community example

```bash
printenv OPENAI_API_KEY | codex login --with-api-key
```

The 1Password Environments MCP server (May 2026) wires `op://` references into Codex sessions, which is the cleanest path today.

## Docs

- [Config reference](https://developers.openai.com/codex/config-reference)
- [Authentication](https://developers.openai.com/codex/auth)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
