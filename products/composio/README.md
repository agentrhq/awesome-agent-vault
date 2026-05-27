---
name: Composio
slug: composio
type: product
license: Apache-2.0
stars: 28482
last_verified: 2026-05-27
maintainer: ComposioHQ
related: [scoped-delegation-tokens, hook-based-injection]
---

# Composio

Toolkit platform with 1000+ pre-built integrations, each carrying its own managed authentication. The vaulting layer is one feature of a larger toolkit hub; for many agent frameworks (LangChain, CrewAI, AutoGen, LlamaIndex) Composio is the path of least resistance for OAuth-backed third-party access.

## Architecture

Per-user (or per-agent) connected accounts. Composio holds the OAuth refresh tokens, mints access tokens on demand, and exposes integration tools to the agent framework. The agent process calls Composio rather than the underlying API; Composio handles auth.

## Who it is for

Teams building on LangChain, CrewAI, AutoGen, LlamaIndex, or other agent frameworks that want OAuth-shaped third-party integrations without implementing each per service.

## Trade-offs

Larger surface than a pure vault. The platform is the source of truth for connected accounts; self-hosting is possible but the SaaS is the common deployment.

## Links

- Repo: [github.com/ComposioHQ/composio](https://github.com/ComposioHQ/composio)
- Last updated: 2026-05-27
- Stars: 28,482
- License: Apache-2.0

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
