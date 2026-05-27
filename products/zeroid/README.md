---
name: zeroid
slug: zeroid
type: product
license: unknown
stars: 140
last_verified: 2026-05-27
maintainer: highflame-ai
related: [non-human-identity, short-lived-tokens]
---

# zeroid

Autonomous Agent Identity Management System (AAIMS). Built around RFC 8693 token exchange and SPIFFE workload identity rather than a static vault model. The unit of work is an identity, not a secret.

## Architecture

Each agent gets a SPIFFE identity. zeroid mints short-lived, narrowly scoped credentials per request via RFC 8693 token exchange. Upstream identity providers vouch for the agent's principal; downstream services see a fresh, scoped token per call.

## Who it is for

Teams running multi-agent systems who want identity-first semantics (who is acting) rather than secret-first semantics (what key did they present). Closer to Microsoft Entra Agent ID and Keycard than to a vault product.

## Trade-offs

SPIFFE and RFC 8693 are heavyweight standards. Solo developers and small teams will find them overkill.

## Links

- Repo: [github.com/highflame-ai/zeroid](https://github.com/highflame-ai/zeroid)
- Last updated: 2026-05-27
- Stars: 140

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
