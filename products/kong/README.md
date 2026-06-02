---
name: Kong AI Gateway
slug: kong
type: product
license: Apache-2.0
stars: 43507
last_verified: 2026-05-28
maintainer: Kong
related: ["hook-based-injection"]
---

# Kong AI Gateway

Kong is an established API gateway that has extended its plugin surface to cover LLM and MCP traffic. It sits in front of upstream APIs and model providers, brokering credentials, applying rate limits, and emitting observability data. The same proxy that fronts internal microservices now also fronts calls to OpenAI, Anthropic, and similar providers, with auth plugins handling key rotation and per-route policy.

## Architecture

Kong runs as a reverse proxy built on OpenResty and Nginx. Clients send requests to a Kong route, and Kong injects credentials, rewrites headers, enforces rate limits, and forwards to the upstream. The AI Gateway adds provider-specific plugins that normalize request and response shapes across LLM vendors. Credentials are stored in Kong's datastore or pulled from external secret managers via plugins. Observability hooks emit logs, metrics, and traces to standard backends. Policy is configured declaratively or through the Admin API.

## Who it is for

Platform teams that already run Kong for internal API traffic and want to extend the same control plane to outbound agent and LLM calls. Useful where a single gateway is preferred for rate limiting, audit, and credential handling across both internal services and third-party AI providers.

## Trade-offs

Kong is a heavier deployment than agent-specific brokers. It assumes a network gateway model, which requires operators comfortable with Nginx, Lua plugins, and a control plane. Provider coverage for non-LLM SaaS APIs is narrower than dedicated agent vaults, and bespoke auth flows often need custom plugin work.

## Links

- Repo: [github.com/Kong/kong](https://github.com/Kong/kong)
- Stars: 43507
- License: Apache-2.0

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
