---
name: sigcli
slug: sigcli
type: product
license: unknown
stars: 233
last_verified: 2026-05-27
maintainer: sigcli
related: [hook-based-injection, per-task-scoping]
---

# sigcli

Authentication CLI and proxy for AI agents. The repo's own framing is "give agents access, not your credentials." Direct overlap with Authsome and Kontext CLI in the local-broker category.

## Architecture

CLI plus a local proxy. The proxy fronts outbound calls; the CLI manages identity, scoping, and per-agent capabilities. The agent process operates against the proxy rather than directly against the upstream API.

## Who it is for

Developers wiring multiple coding agents (Claude Code, Cursor, Codex) into the same set of third-party APIs and wanting a single auth layer.

## Trade-offs

License status not declared on the public repo at time of writing.

## Links

- Repo: [github.com/sigcli/sigcli](https://github.com/sigcli/sigcli)
- Last updated: 2026-05-25
- Stars: 233

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
