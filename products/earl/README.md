---
name: earl
slug: earl
type: product
license: unknown
stars: 113
last_verified: 2026-05-27
maintainer: mathematic-inc
related: [hook-based-injection, secret-redaction]
---

# earl

Rust-based CLI proxy for AI agents. Operations are defined as HCL templates; secrets live in the OS keychain; the proxy includes prompt-injection mitigations at the tool-call boundary.

## Architecture

HCL files declare allowed operations and their bindings. Each operation references secrets by keychain entry; the proxy resolves them at call time. The MCP integration lets MCP-aware agents (Claude Code, Cursor, Windsurf) consume the operations as tools.

## Who it is for

Rust-friendly developers who like declarative operation templates and want the security model baked into the proxy rather than left to the agent.

## Trade-offs

HCL adds a small learning curve. The Rust binary distribution requires a build step or a release download.

## Links

- Repo: [github.com/mathematic-inc/earl](https://github.com/mathematic-inc/earl)
- Last updated: 2026-05-12
- Stars: 113
- Language: Rust

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
