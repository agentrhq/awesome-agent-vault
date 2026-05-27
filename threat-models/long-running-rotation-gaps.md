---
name: Long-running agent rotation gaps
slug: long-running-rotation-gaps
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: scalekit
related: [short-lived-tokens, just-in-time-injection]
---

# Long-running agent rotation gaps

Multi-day agents outlive their tokens. The agent appears healthy, the work appears in progress, but every tool call now returns 401 because the bearer token has expired and nothing in the harness is responsible for refreshing it.

## Surface

- Background agents (research, monitoring, scheduled tasks) running for days.
- OAuth-based integrations with one-hour access tokens and no refresh loop.
- Agents that checkpoint progress but not credential state.

## Mitigations

- A background refresh loop with per-provider expiry tracking. The agent harness, not the agent, owns the refresh.
- Just-in-time injection ([patterns/just-in-time-injection](../patterns/just-in-time-injection.md)) so the agent never holds a token long enough to outlive it.
- Checkpoint credentials alongside task state so the agent can resume after reissue.

## Citation

- [Scalekit: How to handle token refresh for AI agents](https://www.scalekit.com/blog/how-handle-token-refresh-ai-agents)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
