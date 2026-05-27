---
name: AgentGuard
slug: agentguard
type: product
license: unknown
stars: 413
last_verified: 2026-05-27
maintainer: GoPlusSecurity
related: [secret-redaction, sandboxed-egress]
---

# AgentGuard

Runtime guardrail layer for agents. Blocks data loss paths, scrubs secrets from agent context, and maintains a trust registry for skills and tools. Closer to a "DLP for agents" than a vault.

## Architecture

Hooks into the agent's tool-call surface. Each call is matched against rules: known credential patterns are redacted, untrusted skills are gated, and outbound payloads are scanned before they leave the trust boundary.

## Who it is for

Teams running agents in production who want a runtime check layer in addition to a vault. Sits next to a vault rather than replacing one.

## Trade-offs

Guardrails are detection-shaped. They reduce the blast radius of a slip but do not replace structural controls like just-in-time injection.

## Links

- Repo: [github.com/GoPlusSecurity/agentguard](https://github.com/GoPlusSecurity/agentguard)
- Last updated: 2026-05-27
- Stars: 413

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
