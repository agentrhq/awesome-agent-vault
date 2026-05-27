---
name: Just-in-time credential injection
slug: just-in-time-injection
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: hashicorp
related: [hook-based-injection, short-lived-tokens]
---

# Just-in-time credential injection

The agent should not hold the secret. A broker issues a dynamic, role-scoped credential at the moment of the tool call, valid for minutes, and revokes it once the call returns. The agent observes only the tool's response, never the underlying API key.

## Why it matters

This collapses the surface for the entire class of "what if the model echoes the secret back" concerns to zero for that credential. Even if a session is later compromised, the credential it briefly used is already invalid.

## Reference implementation

HashiCorp Vault's validated pattern for AI agent identity is the most fully documented example. Vault Agent sidecars template per-lease credentials into the agent process; the lease ends when the call ends.

Authsome ([products/authsome](../products/authsome/)) implements the same model at the local-proxy layer for solo and small-team setups where Vault is too heavy.

## Citation

- [HashiCorp: AI agent identity with HashiCorp Vault](https://developer.hashicorp.com/validated-patterns/vault/ai-agent-identity-with-hashicorp-vault)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
