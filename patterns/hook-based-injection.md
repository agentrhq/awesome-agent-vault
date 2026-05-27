---
name: Hook-based injection
slug: hook-based-injection
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: authsome
related: [just-in-time-injection, per-task-scoping]
---

# Hook-based injection

Resolve credential placeholders at the tool boundary, not in prompt context. The agent's code emits requests with placeholder tokens (`__stripe_key__`, `__github_pat__`); a hook intercepts each tool invocation and swaps placeholders for real values before the call leaves the trust boundary.

## Why it matters

Two properties follow from this shape. First, the secret never appears in the model's context window, so it cannot be elicited back through clever prompting. Second, the hook is the single chokepoint for audit, redaction, and policy.

## Reference implementation

Authsome's local proxy ([products/authsome](../products/authsome/)) implements this for the Claude Code, Cursor, and Codex CLIs through the platform hook surfaces each provides (Claude Code hooks, MCP server env, Cursor's `${env:VAR}` interpolation).

Infisical Agent Vault ([products/infisical-agent-vault](../products/infisical-agent-vault/)) implements it at the HTTPS proxy layer for environments where shimming the agent process is preferable to shimming the platform.

## Citation

- [Anthropic: Claude Code hooks complete guide](https://claudefa.st/blog/tools/hooks/hooks-guide)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
