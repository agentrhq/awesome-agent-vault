---
name: Subagent credential non-inheritance
slug: subagent-non-inheritance
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: anthropic
related: [confused-deputy, per-task-scoping]
---

# Subagent credential non-inheritance

By default, spawned subagents start with the narrowest credential surface their role requires, not the parent's full set. A summarizer subagent should not silently gain database write capability because its parent had it.

## Mechanics

The parent agent declares what the subagent is for; the broker provisions a credential set scoped to that purpose. The subagent inherits nothing else. When the subagent finishes, its credentials revoke independently of the parent's.

## Reference implementation

Claude Code applies this in practice today: Task-spawned subagents do not inherit MCP server tools unless explicitly granted, and plugin subagents cannot define their own `mcpServers` or `permissionMode`. The platform enforces least-privilege per agent role rather than per agent process.

## Citation

- [Claude Code subagent MCP access (issue #34935)](https://github.com/anthropics/claude-code/issues/34935)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
