---
name: psst
slug: psst
type: product
license: unknown
stars: 224
last_verified: 2026-05-27
maintainer: Michaelliv
related: [token-substitution-proxy, hook-based-injection]
---

# psst

AI-native secrets manager that uses the OS keychain as the backing store and a token-substitution model on top. The agent operates on opaque placeholders; psst resolves them to real values only at the outbound network boundary.

## Architecture

Local daemon backed by Keychain (macOS), Credential Manager (Windows), or kwallet/secret-service (Linux). Secrets are referenced by name in agent code; psst substitutes the real value at the proxy layer. The agent never observes the plaintext.

## Who it is for

Developers who want a no-extra-vault setup, leaning on the OS keychain. Particularly comfortable for macOS users who already trust Keychain.

## Trade-offs

OS keychain bias means cross-machine and team-shared workflows need additional plumbing.

## Links

- Repo: [github.com/Michaelliv/psst](https://github.com/Michaelliv/psst)
- Last updated: 2026-05-25
- Stars: 224

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
