---
name: Subagent credential inheritance
slug: subagent-inheritance
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [subagent-non-inheritance, confused-deputy]
---

# Subagent credential inheritance

Spawned subagents inherit more privilege than their role needs. The harness gives child agents the parent's full environment as a convenience; that convenience widens the blast radius of any compromise.

## Surface

- Multi-agent harnesses that pass `os.environ` to every subagent.
- MCP servers configured at the parent level and silently available to spawned tasks.
- Plugin-style subagents that can declare their own permission mode.

## Mitigations

- Provision credentials per subagent role, not per agent process. See [patterns/subagent-non-inheritance](../patterns/subagent-non-inheritance.md).
- Use a broker rather than process inheritance. The subagent asks the broker for what it needs; the broker decides whether to grant.
- Audit MCP server access per role and remove the silent default.

## Citation

- [Claude Code subagent MCP access issue](https://github.com/anthropics/claude-code/issues/34935)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
