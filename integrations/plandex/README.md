---
name: Plandex
slug: plandex
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-28
maintainer: plandex-ai
related: []
---

# Plandex

Plandex is an open-source terminal-based coding agent that plans and executes multi-file changes across a project. It runs locally against any provider supported by its model router and reads provider credentials directly from the shell environment. The credential model mirrors Aider and Crush: no hook system, no first-party secrets store, just env vars.

## Default mechanism

- Provider API keys read from environment variables (`OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, `OPENROUTER_API_KEY`, etc.).
- Optional self-hosted Plandex server reads the same env vars at process start.
- No config file holds secrets. Model selection is per-plan, but auth is global to the shell.

## Injection surface

None at the application layer. A vault product injects by populating the environment before `plandex` starts, either via a wrapper command, a shell hook, or a sidecar that exports keys into the process. There is no plugin API, no MCP credential source, and no callback for refresh.

## Notes

Plandex is commonly paired with multiple providers in one session (planner on one model, executor on another), so the env must carry several keys at once. Use a single vault entry per provider and inject the whole set at launch rather than swapping mid-session. The self-hosted server variant inherits the same model and benefits from the same wrapper pattern.

## Docs

- Repo: [github.com/plandex-ai/plandex](https://github.com/plandex-ai/plandex)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
