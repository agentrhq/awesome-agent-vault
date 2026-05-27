---
name: Infisical Agent Vault
slug: infisical-agent-vault
type: product
license: proprietary (source-available)
stars: 1440
last_verified: 2026-05-27
maintainer: Infisical
related: [hook-based-injection, just-in-time-injection, claude-code]
---

# Infisical Agent Vault

HTTPS proxy that swaps placeholder tokens for real third-party credentials at the network layer. The agent process never holds a real secret; the proxy substitutes them on outbound requests and strips them from logs.

## Architecture

Listens on `:14322` by default. The agent reads placeholder values (`__anthropic_api_key__`, `__github_pat__`) from its environment and emits HTTPS calls through the proxy. The proxy authenticates the outbound destination against an Infisical project and injects the real credential server-side. Inbound responses are returned unchanged.

## Who it is for

Engineering teams already running Infisical for shared secret management who want the same control plane for coding agents in production. Particularly strong for Claude Code, OpenClaw, Hermes, and custom harnesses.

## Trade-offs

The proxy-only model means tools must speak HTTP through it. Non-HTTP integrations (raw sockets, bespoke binaries) break unless they can be wrapped. Anything that needs the raw secret in-process (signing a JWT locally, for example) also breaks.

## Example

```bash
infisical agent-vault start --project-id $INFISICAL_PROJECT_ID
HTTPS_PROXY=http://localhost:14322 claude
```

## Links

- Repo: [github.com/Infisical/agent-vault](https://github.com/Infisical/agent-vault)
- Latest release: v0.22.0 (2026-05-26)
- License: source-available (NOASSERTION on GitHub)
- Language: Go

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
