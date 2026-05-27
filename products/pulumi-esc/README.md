---
name: Pulumi ESC
slug: pulumi-esc
type: product
license: Apache-2.0
stars: 284
last_verified: 2026-05-27
maintainer: pulumi
related: [hook-based-injection]
---

# Pulumi ESC

Environments, Secrets, and Configuration service that composes secrets from multiple backends (Vault, AWS Secrets Manager, 1Password, others) and exposes them through `esc run`. Useful when a team already standardizes on Pulumi for IaC.

## Architecture

ESC defines "environments" that can reference secrets from any supported backend. `esc run <command>` resolves the environment and injects secrets into the wrapped process. The composition layer is the value; ESC itself does not need to be the source of truth.

## Who it is for

IaC teams using Pulumi who want one config plane across multiple secret stores. Agent runs become just another consumer.

## Trade-offs

Same env-injection trade-off as Doppler. The agent process holds plaintext secrets in memory; there is no per-tool-call brokering.

## Example

```bash
esc run agent-prod -- claude
```

## Links

- Repo: [github.com/pulumi/esc](https://github.com/pulumi/esc)
- Latest release: v0.24.0 (2026-05-15)
- License: Apache-2.0
- Language: Go

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
