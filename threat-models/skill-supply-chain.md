---
name: Skill and tool supply-chain
slug: skill-supply-chain
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [subagent-inheritance, secret-redaction]
---

# Skill and tool supply-chain

Skills and tools installed from third-party marketplaces inherit the agent's credential surface. A skill with hidden behavior can use that surface to disclose secrets, the same way a malicious npm package can read `process.env`.

## Surface

- Agent skill marketplaces with limited review.
- MCP server registries that any author can publish to.
- npm/pip tools that the agent installs on demand.

## Worked example

A 2026 audit of agent skill ecosystems reported that a substantial fraction of public skills contained patterns associated with secret disclosure or unscoped network calls. The findings span legitimately misconfigured skills and ones that appear written to extract credentials from the host agent.

## Mitigations

- Install skills from a reviewed registry. Pin versions. Audit transitive dependencies.
- Use [patterns/subagent-non-inheritance](../patterns/subagent-non-inheritance.md): a skill is a subagent role, not a sibling of the parent. It should not inherit credentials it does not declare a need for.
- Apply [patterns/secret-redaction](../patterns/secret-redaction.md) at the skill boundary so secrets the skill does not need are not in its environment in the first place.
- Tools like [AgentGuard](../products/agentguard/) maintain a trust registry for skills as a runtime check layer.

## Citation

- [Snyk ToxicSkills audit discussion](https://www.reddit.com/r/SecOpsDaily/comments/1qz3w78/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
