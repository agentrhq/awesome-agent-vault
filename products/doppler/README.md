---
name: Doppler
slug: doppler
type: product
license: Apache-2.0
stars: 373
last_verified: 2026-05-27
maintainer: DopplerHQ
related: [hook-based-injection]
---

# Doppler

CLI that pulls a project's secrets from Doppler's SaaS and injects them as environment variables into a wrapped process. Familiar to teams already using Doppler for application config.

## Architecture

`doppler run -- <command>` reads secrets from a configured project and config, then exec's the command with the secrets in `process.env`. The CLI is local; the source of truth is the SaaS.

## Who it is for

Small and mid-sized teams using Doppler as the project secret store who want a `doppler run -- claude` style workflow.

## Trade-offs

Env-var injection means the agent process holds the raw secret in memory for its entire run. There is no per-request brokering, no JIT, no per-tool-call redaction. Better than nothing, weaker than a proxy.

## Example

```bash
doppler run --project agent-prod --config prd -- claude
```

## Links

- Repo: [github.com/DopplerHQ/cli](https://github.com/DopplerHQ/cli)
- Latest release: 3.76.0 (2026-04-22)
- License: Apache-2.0
- Language: Go

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
