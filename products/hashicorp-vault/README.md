---
name: HashiCorp Vault
slug: hashicorp-vault
type: product
license: BUSL-1.1
stars: 35666
last_verified: 2026-05-27
maintainer: hashicorp
related: [just-in-time-injection, short-lived-tokens, audit-trails-siem]
---

# HashiCorp Vault

General-purpose enterprise secrets manager. HashiCorp publishes a validated pattern for "AI Agent Identity with Vault" that issues dynamic, role-scoped credentials at the moment of a tool call, valid for minutes, revoked after use.

## Architecture

Vault Agent sidecars run alongside agent processes. The sidecar templates secrets into the process environment or files; for dynamic backends, the secret is minted at lease start and revoked at lease end. The agent never holds long-lived credentials.

## Who it is for

Enterprises already running Vault who want to extend the existing control plane to agent workloads.

## Trade-offs

Vault is not designed for ad-hoc per-tool-call brokering. Bolting agent UX onto it requires custom glue (the validated pattern is a starting point, not a turnkey product).

## Example

```bash
# Mint a 10-minute database credential for an agent task
vault read database/creds/agent-readonly
```

## Links

- Repo: [github.com/hashicorp/vault](https://github.com/hashicorp/vault)
- AI Agent Identity validated pattern: [developer.hashicorp.com/validated-patterns/vault/ai-agent-identity-with-hashicorp-vault](https://developer.hashicorp.com/validated-patterns/vault/ai-agent-identity-with-hashicorp-vault)
- Latest release: v3.13.1 (2026-05-16)
- License: BUSL-1.1
- Language: Go

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
