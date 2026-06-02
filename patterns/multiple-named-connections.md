---
name: Multiple named connections per provider
slug: multiple-named-connections
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: authsome
related: ["per-task-scoping"]
---

# Multiple named connections per provider

A single agent operator commonly holds more than one account at the same provider. Work and personal GitHub, dev and prod Stripe, several Slack workspaces, two Linear orgs. The pattern requires the credential broker to register each account as a distinct named connection under the same provider, so the agent can pick the right one by name. Without it, the operator falls back to swapping a single global token between sessions, which loses context and invites mistakes.

## Mechanics

Each connection is stored as a tuple of provider, connection name, and credential material. When the agent issues a call, the broker resolves the request against the named connection rather than a default global token. Names are operator-chosen labels such as `github-personal`, `github-work`, `stripe-dev`, `stripe-prod`. The agent receives capability to address connections by name, and the broker enforces that the chosen name maps to a credential the current task is permitted to use. Listing, adding, and removing connections happens out of band, through the broker's CLI or UI, never through the agent itself.

## Reference implementation

Authsome stores connections as `provider:name` pairs in its local keyring and exposes them to agents through a connection selector. See [sites/authsome.ai/README.md](../sites/authsome.ai/README.md) for the entry.

## Citation

- [Authsome multiple connections guide](https://authsome.ai/docs/guides/multiple-connections.md)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
