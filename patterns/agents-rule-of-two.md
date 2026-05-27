---
name: Agents Rule of Two
slug: agents-rule-of-two
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: meta
related: [lethal-trifecta, per-task-scoping]
---

# Agents Rule of Two

Meta's October 2025 framework formalizes the lethal trifecta into an operational rule. Until robust defenses against untrusted instructions exist, an agent session should hold at most two of: untrusted input, sensitive data access, state change or external communication.

## Applied to credentials

A session reading attacker-controlled text should not simultaneously hold long-lived secrets and an outbound network capability. Concretely:

- Triage session: untrusted input + read-only data, no write capability and no network.
- Reporting session: sensitive data + outbound (one fixed destination), no untrusted text in context.
- Workflow session: state change + untrusted input, no broad data access.

## Reference implementation

Meta uses the rule internally as a gating policy for agent deployments. Open implementations are emerging in 2026; the most direct expression is a policy engine that inspects the proposed tool surface against the three categories before granting credentials.

## Citation

- [Meta AI: Practical AI Agent Security](https://ai.meta.com/blog/practical-ai-agent-security/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
