---
name: Authsome
slug: authsome
type: product
license: MIT
stars: 38
last_verified: 2026-05-27
maintainer: agentrhq
related: [per-task-scoping, hook-based-injection, claude-code, codex, cursor]
---

# Authsome

Local OAuth2 and API-key vault for agents. The developer logs in once per provider; every connected agent (Claude Code, Cursor, Codex, others) stays authenticated through Authsome without ever seeing the raw credential.

## Architecture

Authsome ships a local proxy process and a CLI. The proxy fronts outbound HTTPS calls; placeholder tokens in agent code are swapped for real credentials at the network boundary. Agents call `https://api.stripe.com/...` through the proxy, get back the real response, and never observe the secret.

## Who it is for

Solo developers and small teams using one or more coding agents who want a local, no-SaaS auth layer for third-party APIs. The default install is one binary plus a config directory.

## Trade-offs

Local-first and headless. There is no built-in centralized audit dashboard or team RBAC. Teams that need shared audit trails across many developers will want a hosted layer alongside (HashiCorp Vault, Infisical, or a SaaS).

## Example

```bash
pip install authsome
authsome login linear
authsome run claude
```

Inside the running agent, calls to Linear go through the local proxy; the agent code reads a placeholder token (`__linear_token__`) that the proxy substitutes on outbound requests.

## Links

- Repo: [github.com/agentrhq/authsome](https://github.com/agentrhq/authsome)
- Docs: [authsome.dev](https://authsome.dev)
- Latest release: v0.4.2 (2026-05-25)
- License: MIT
- Language: Python

## Maintainer disclosure

This list is curated by Authsome. See [CATEGORY-MAP.md](../../CATEGORY-MAP.md) for how the maintainer relationship is handled.

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
