---
name: onecli
slug: onecli
type: product
license: Apache-2.0
stars: 2260
last_verified: 2026-05-27
maintainer: onecli
related: [hook-based-injection, just-in-time-injection]
---

# onecli

Open-source credential gateway with a built-in vault that fronts agent tool calls and injects keys on the way out. Distributed as a single binary, which makes it the lowest-friction option for solo developers.

## Architecture

`onecli` runs locally and wraps the agent process. Outbound HTTPS calls are intercepted; the gateway looks up the real credential in its built-in vault and substitutes it before the call leaves the machine. There is no separate vault to run.

## Who it is for

Solo developers and small teams running CLI coding agents who want one binary instead of self-hosting Vault or paying for a SaaS.

## Trade-offs

The built-in vault simplifies setup, but it is yet another secret store to keep alongside whatever the team already uses (1Password, Vault, Doppler). Teams with an existing secret store will find the value lower.

## Example

```bash
onecli vault add stripe sk_live_...
onecli run -- claude
```

## Links

- Repo: [github.com/onecli/onecli](https://github.com/onecli/onecli)
- Latest release: v1.31.1 (2026-05-26)
- License: Apache-2.0
- Language: TypeScript

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
