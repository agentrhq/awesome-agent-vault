---
name: Tool-use credential confusion
slug: tool-use-credential-confusion
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [confused-deputy, per-task-scoping]
---

# Tool-use credential confusion

An agent invokes a tool with the wrong principal's credentials. The mistake is structural rather than malicious: the executor's identity stands in for the requester's, and the tool runs at the wrong privilege level.

## Surface

Multi-agent systems where a parent agent executes on behalf of a subagent without re-authenticating the requester. Also: shared service accounts where multiple agents present the same identity to a tool, so the tool cannot distinguish which agent asked.

## Mitigations

- Authenticate the requesting agent at every privilege boundary. See [patterns/confused-deputy](../patterns/confused-deputy.md).
- Issue per-agent identities rather than shared service accounts. See [patterns/audit-trails-siem](../patterns/audit-trails-siem.md).
- Apply [patterns/subagent-non-inheritance](../patterns/subagent-non-inheritance.md) so a subagent's credential set is provisioned to its role, not inherited from the parent.

## Citation

- [SANS: AI agent as a confused deputy](https://www.sans.org/blog/your-ai-agent-easily-confused-deputy-why-cloud-security-needs-credential-broker)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
