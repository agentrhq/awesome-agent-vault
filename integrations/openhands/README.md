---
name: OpenHands
slug: openhands
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-27
maintainer: All-Hands-AI
related: [sandboxed-egress]
---

# OpenHands

Sandboxed coding agent runtime (formerly OpenDevin). Each task runs inside a container; credentials flow via environment variables and a configurable secret-loading hook.

## Default mechanism

- Container env vars at task start.
- `config.toml` for model provider settings.

## Injection surface

The container boundary is a natural injection point. A sidecar proxy (Infisical Agent Vault, Authsome, onecli) running outside the sandbox can inject credentials at the egress layer.

## Notes

The container model makes this one of the better integration targets for vault products: a proxy on the host can mediate every outbound call from the sandbox without trusting the agent process.

## Docs

- Repo: [github.com/All-Hands-AI/OpenHands](https://github.com/All-Hands-AI/OpenHands)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
