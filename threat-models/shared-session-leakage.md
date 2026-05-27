---
name: Shared-session leakage
slug: shared-session-leakage
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [per-task-scoping, audit-trails-siem]
---

# Shared-session leakage

Multi-tenant agents that share a single session or process boundary can let one tenant's secrets bleed into another's context. The cause is usually accidental: a global cache, a logging singleton, an LLM context window reused across requests.

## Surface

- Hosted agent platforms serving multiple end-users from one process.
- Conversation memory implementations that key on agent rather than on user.
- Logging or tracing systems that aggregate across tenants without scrubbing identifiers.

## Mitigations

- One credential per task per user; no global credential store accessible from request handlers. See [patterns/per-task-scoping](../patterns/per-task-scoping.md).
- Per-user identity in audit logs so SIEM rules can detect cross-tenant patterns. See [patterns/audit-trails-siem](../patterns/audit-trails-siem.md).
- Wipe context, caches, and tool state between tenant requests.

## Citation

- [Meta AI: Practical AI Agent Security](https://ai.meta.com/blog/practical-ai-agent-security/)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
