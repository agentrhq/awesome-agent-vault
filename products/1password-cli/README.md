---
name: 1Password CLI
slug: 1password-cli
type: product
license: proprietary
stars: n/a
last_verified: 2026-05-27
maintainer: 1Password
related: [hook-based-injection, scoped-delegation-tokens]
---

# 1Password CLI

`op run` substitutes `op://` secret references in environment variables with real secrets at process start. The May 2026 Environments MCP server extends the same model to Codex and Cursor.

## Architecture

The CLI authenticates to 1Password using a biometric prompt or service account. References like `op://Vault/Item/field` get resolved on `op run`; the secret only enters the wrapped process's environment for the duration of that process.

## Who it is for

1Password customers, especially Codex and Cursor users via the new Environments MCP server.

## Trade-offs

The CLI itself is closed source; the agent story depends on a 1Password subscription. For agents that need credentials brokered per tool call rather than per process, `op run` is too coarse.

## Example

```bash
# In .env: STRIPE_KEY=op://Engineering/Stripe/api_key
op run --env-file .env -- claude
```

## Links

- Site: [1password.com/developers/command-line](https://developer.1password.com/docs/cli/)
- Environments MCP server (May 2026): [1password.com/press/2026/may/openai-codex-integration](https://1password.com/press/2026/may/openai-codex-integration)
- License: proprietary
- Language: Go binary

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
