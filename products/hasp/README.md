---
name: hasp
slug: hasp
type: product
license: unknown
stars: 455
last_verified: 2026-05-27
maintainer: gethasp
related: [just-in-time-injection, hook-based-injection]
---

# hasp

Local-first broker for managed secrets in agent workflows. Go binary, designed around the broker model rather than a static secret store: the agent asks for a secret by name, hasp resolves it from a configured backend and returns it for the duration of one operation.

## Architecture

A local daemon plus CLI. Backends are pluggable; the broker is the abstraction. The agent process never persists secrets across calls.

## Who it is for

Developers running coding agents locally who want a broker shape without running HashiCorp Vault. Familiar to teams who like the daemon-plus-CLI ergonomics of Doppler or onecli but want broker semantics.

## Trade-offs

License is not declared on the public repo at time of writing. Treat as source-available until clarified.

## Links

- Repo: [github.com/gethasp/hasp](https://github.com/gethasp/hasp)
- Last updated: 2026-05-26
- Stars: 455
- Language: Go

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
