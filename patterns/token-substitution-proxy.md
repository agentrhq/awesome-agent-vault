---
name: Token substitution proxy
slug: token-substitution-proxy
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: psst
related: [hook-based-injection, secret-redaction]
---

# Token substitution proxy

A variant of hook-based injection where the agent operates entirely on opaque placeholders (`phm_abc123`, `__secret_42__`) and never sees the real value at any point in the call chain. The proxy substitutes the real value at the outbound network boundary and substitutes the placeholder back into any response that echoes the credential.

## Why it is distinct from hook-based injection

Pure hook-based injection resolves placeholders on the way out. Token substitution adds the symmetric step on the way in: if a downstream API ever returns the credential (intentionally or by accident), the proxy substitutes it back to a placeholder before the response reaches the agent. The agent's view of the credential is consistent: an opaque token, end to end.

This closes a class of disclosure paths that pure outbound injection leaves open. If the API ever reflects the bearer token in an error message, the agent context still does not see the real value.

## Reference implementations

- [psst](../products/psst/) implements the symmetric model on the OS keychain.
- [phantom-secrets](https://github.com/ashlrai/phantom-secrets) is a tiny worked example: real secrets become `phm_*` tokens at both boundaries.
- [earl](../products/earl/) uses the same shape on top of HCL operation templates.

## Citation

- [psst on GitHub](https://github.com/Michaelliv/psst)
- [phantom-secrets on GitHub](https://github.com/ashlrai/phantom-secrets)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
