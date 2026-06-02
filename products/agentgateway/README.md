---
name: agentgateway
slug: agentgateway
type: product
license: Apache-2.0
stars: 2981
last_verified: 2026-05-28
maintainer: agentgateway
related: ["hook-based-injection","sandboxed-egress"]
---

# agentgateway

agentgateway is a Rust-based agentic proxy that sits between AI agents and the MCP servers, APIs, and other agents they call. It positions itself explicitly as an MCP gateway, terminating agent traffic and re-emitting it to upstream services with credentials injected at the proxy layer. The agent process itself never sees the secret, only the gateway endpoint and a session-scoped identity.

## Architecture

The gateway runs as a standalone Rust binary or sidecar in front of MCP servers and HTTP tool endpoints. Agents are pointed at the gateway rather than at upstream services directly. Inbound requests are authenticated against the gateway's own identity model, then matched to upstream routes where the gateway attaches the real upstream credentials, applies policy (rate limits, tool allow-lists, payload filters), and forwards the call. Responses flow back through the same path, so audit and redaction can happen on egress as well as ingress.

## Who it is for

Platform and infra teams operating MCP servers or agent fleets in production who want a single, language-agnostic enforcement point for auth, policy, and observability. It fits environments where agents are already deployed behind a proxy or service mesh and where adding a per-agent library is not feasible.

## Trade-offs

Running a proxy adds a network hop and an operational component to keep highly available. Credential injection at the gateway means the gateway itself becomes a high-value target and a single point of compromise, so it has to be hardened, logged, and rotated with the same discipline as a secrets manager. Local development against the gateway also requires the proxy to be running.

## Links

- Repo: [github.com/agentgateway/agentgateway](https://github.com/agentgateway/agentgateway)
- Stars: 2981
- License: Apache-2.0

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
