---
name: Stripe
slug: stripe
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: stripe
related: [scoped-delegation-tokens, per-task-scoping]
---

# Stripe

Stripe is one of the strongest references for agent-ready credentials. The platform ships [Restricted API Keys](https://docs.stripe.com/keys/restricted-api-keys) (RAKs), prefixed `rk_`, that the documentation explicitly recommends "when giving a key to an AI agent."

## Credential types

- **Restricted keys** (`rk_`): per-resource Read / Write / None. The right default for agents.
- **Secret keys** (`sk_`): full account access. Do not hand to an agent.
- **Publishable keys** (`pk_`): client-side, no PII access.
- **Organization keys** (`sk_org_`): for the new multi-account organization model.
- **OAuth Connect**: 1h access token + refresh, plus `Stripe-Account` header for platforms acting on behalf of connected accounts.

## Recommended pattern

Mint one Restricted Key per agent with Read-only on the minimum resource set. For Connect platforms, use a short-lived OAuth access token and rotate via the refresh token. Avoid placing `sk_` keys in any process that ingests model output.

## Critical scopes to refuse

`charges:write`, `customers:write`, `payouts:write`, `transfers:write`, `setup_intents:write`, `terminal:write`. For Connect: `read_write` instead of `read_only`.

## Rotation

Rotate RAKs quarterly or on team change. OAuth access tokens auto-rotate hourly. Connect refresh tokens are long-lived; rotate on incident.

## Example

```bash
# Read-only RAK with customers:read and charges:read
curl https://api.stripe.com/v1/customers/cus_X \
  -u rk_live_51Hxx...:
```

## Docs

- [Restricted API keys](https://docs.stripe.com/keys/restricted-api-keys)
- [API keys overview](https://docs.stripe.com/keys)
- [Connect OAuth reference](https://docs.stripe.com/connect/oauth-reference)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
