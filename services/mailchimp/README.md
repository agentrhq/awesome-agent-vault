---
name: Mailchimp
slug: mailchimp
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: mailchimp
related: [scoped-delegation-tokens]
---

# Mailchimp

Mailchimp's Marketing API authenticates with long-lived API keys that embed the account's data center as a suffix (for example, `abc123-us1`). The suffix is not a secret on its own, but it routes requests to the correct shard and must travel with the key. OAuth2 exists for partner apps, but most direct integrations and internal automations rely on the API key model.

## Credential types

- API key with data center prefix (e.g. `-us1`, `-us6`, `-us21`)
- OAuth2 access tokens (for registered partner applications)
- Mandrill API keys (transactional, separate product and credential pool)

## Recommended pattern

For agent use, mint a dedicated API key per agent under a service user with the minimum required role (Author or Manager, not Owner). Inject the key at request time and never persist it to disk. If the integration is user-facing and distributed, prefer OAuth2 so each end user grants their own account.

## Critical scopes to refuse

Mailchimp API keys are unscoped and inherit the full role of the user that minted them. Refuse keys minted from Owner accounts. Refuse access to billing endpoints, account export, and audience deletion paths. Avoid keys tied to a human's primary login.

## Rotation

Rotate API keys every 60 to 90 days, and immediately on agent retirement or suspected exposure. Rotation is manual through Account · Extras · API keys; there is no programmatic rotation endpoint, so schedule it.

## Docs

- [Official docs](https://mailchimp.com/developer/marketing/guides/quick-start/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
