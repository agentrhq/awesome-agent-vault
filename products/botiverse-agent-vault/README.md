---
name: Botiverse agent-vault
slug: botiverse-agent-vault
type: product
license: Apache-2.0
stars: 387
last_verified: 2026-05-27
maintainer: botiverse
related: [hook-based-injection]
---

# Botiverse agent-vault

Lightweight local proxy and wrapper that keeps secrets hidden from chat agents while letting them call APIs. The repo has not been pushed since February 2026, so consider it lightly maintained.

## Architecture

A local wrapper process holds the credentials; the agent calls APIs through the wrapper. The wrapper redacts the credential from any output before returning to the agent. Simpler than the proxy approach used by Infisical or onecli; closer to a tool shim than a true credential broker.

## Who it is for

Hobbyists and developers prototyping agents on a laptop who want a quick way to keep secrets out of prompt context.

## Trade-offs

Maintenance has slowed. Last push was 2026-02-19. Suitable for prototypes; teams should evaluate active alternatives (onecli, Authsome, Infisical Agent Vault) for production.

## Links

- Repo: [github.com/botiverse/agent-vault](https://github.com/botiverse/agent-vault)
- Latest release: v0.4.0 (2026-02-19)
- License: Apache-2.0
- Language: TypeScript

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
