---
name: Non-Human Identity (RFC 8693, SPIFFE)
slug: non-human-identity
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: ietf
related: [scoped-delegation-tokens, short-lived-tokens, audit-trails-siem]
---

# Non-Human Identity (RFC 8693, SPIFFE)

Treat each agent as a first-class principal with its own identity, not as an anonymous holder of a service account key. RFC 8693 (OAuth 2.0 Token Exchange) and SPIFFE (Secure Production Identity Framework For Everyone) provide the standards-based shape for this.

## Mechanics

Each agent runs under a SPIFFE identity issued by a workload-API server. When the agent needs to call a downstream service, it exchanges its identity for a downstream-scoped token using RFC 8693. The downstream service sees a token that names *this* agent, scoped to *this* call, expiring in minutes.

This is structurally different from "the agent holds a long-lived key." There is no key to share, leak, or rotate; there is an identity, and access is the result of policy applied to that identity at each call.

## Reference implementations

- [zeroid](../products/zeroid/) implements the model with RFC 8693 plus SPIFFE for self-hosted setups.
- [Keycard](https://www.helpnetsecurity.com/2026/05/15/keycard-for-multi-agent-apps/) and [Descope Agentic Identity Hub](https://www.helpnetsecurity.com/2026/01/27/descope-agentic-identity-hub-2-0/) implement the model as SaaS.
- Microsoft Entra Agent ID is the enterprise-IdP version.

## Citations

- [RFC 8693: OAuth 2.0 Token Exchange](https://datatracker.ietf.org/doc/html/rfc8693)
- [SPIFFE specification](https://spiffe.io/docs/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
