---
name: Continue.dev
slug: continue-dev
type: integration
license: Apache-2.0
stars: n/a
last_verified: 2026-05-27
maintainer: continuedev
related: [hook-based-injection]
---

# Continue.dev

Continue's `config.yaml` (the new format; `config.json` is deprecated) accepts `${{ secrets.NAME }}` mustache syntax that resolves from `.env`, the workspace `.env`, and the Mission Control hub.

## Default mechanism

- `config.yaml` with `${{ secrets.NAME }}` references.
- Secrets resolved from local `.env`, workspace `.continue/.env`, then Mission Control hub (in that order).

## Injection surface

- MCP servers in the same config reuse the same `${{ secrets.X }}` syntax.
- Mission Control hub provides team-shared secret management.

## Known issue

The IDE extension cannot read shell environment variables, only the configured secret sources. Users who set a secret in their shell rather than `.env` see it silently fail. [Issue #5902.](https://github.com/continuedev/continue/issues/5902)

## Best community example

[Mission Control secrets docs](https://docs.continue.dev/mission-control/secrets/secret-types) describe hub-managed secrets that are shared across team members.

## Docs

- [Config reference](https://docs.continue.dev/reference)
- [Secret types](https://docs.continue.dev/mission-control/secrets/secret-types)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
