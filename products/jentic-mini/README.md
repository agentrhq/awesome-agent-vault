---
name: jentic-mini
slug: jentic-mini
type: product
license: unknown
stars: 124
last_verified: 2026-05-27
maintainer: jentic
related: [hook-based-injection, just-in-time-injection]
---

# jentic-mini

Self-hosted API execution layer that injects credentials at runtime between the agent and the third-party API. Repo topics include `vault`, `credential-manager`, `secrets-management`.

## Architecture

Sits in the call path between the agent and the external API. The agent emits structured tool calls; jentic-mini resolves the credentials from its store and dispatches the actual outbound HTTPS request, returning only the response payload.

## Who it is for

Teams wanting a self-hosted, framework-neutral credential broker that also handles API call orchestration. Bridges the gap between a pure vault and an MCP-style execution layer.

## Trade-offs

License not declared on the public repo at time of writing. The execution-layer scope means it does more than vaulting; teams who only need credential brokering may want a lighter tool.

## Links

- Repo: [github.com/jentic/jentic-mini](https://github.com/jentic/jentic-mini)
- Last updated: 2026-05-27
- Stars: 124

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
