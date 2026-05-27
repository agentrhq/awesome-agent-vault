---
name: LiteLLM Agent Platform
slug: litellm-agent-platform
type: product
license: MIT
stars: 514
last_verified: 2026-05-27
maintainer: BerriAI
related: [sandboxed-egress, hook-based-injection]
---

# LiteLLM Agent Platform

Self-hosted platform that runs coding agents (Claude Code, Codex, Hermes, others) in isolated sandboxes with a built-in vault proxy for outbound API calls. The vault is one feature of a larger sandbox platform rather than a standalone product.

## Architecture

Each agent runs inside an isolated container; outbound HTTPS is routed through a vault proxy that injects credentials and enforces domain allowlists. Multi-tenant by default; one platform instance can serve many users.

## Who it is for

Platform teams who want to run coding agents server-side for many users. The "agents as a service" shape.

## Trade-offs

Heavier to deploy than a pure proxy. If the team only needs credential injection (not sandboxing, not multi-tenancy, not a control plane), a pure proxy product is lighter.

## Example

```bash
docker compose -f litellm-agent-platform/docker-compose.yml up -d
```

## Links

- Repo: [github.com/BerriAI/litellm-agent-platform](https://github.com/BerriAI/litellm-agent-platform)
- Latest release: v1.7.3 (2026-05-26)
- License: MIT
- Language: TypeScript

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
