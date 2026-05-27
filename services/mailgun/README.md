---
name: Mailgun
slug: mailgun
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: mailgun
related: [scoped-delegation-tokens]
---

# Mailgun

Mailgun separates the account's primary API key from domain-scoped sending keys and supports RBAC sub-keys. The sending key is the right shape for agents.

## Credential types

- **Primary API key**: full account access. Keep out of agent reach.
- **Domain sending keys**: bound to one verified domain, restricted to send endpoints.
- **RBAC sub-keys**: role-scoped.

## Recommended pattern

One domain sending key per agent, restricted to `/messages` on the agent's specific domain. Programmatically rotate via the Domain Keys API on deploy.

## Critical scopes to refuse

Primary key usage in any agent process. Any domain other than the one assigned to the agent.

## Rotation

Rotate sending keys per deploy via the Domain Keys API. The API supports key rotation as a first-class operation.

## Example

```bash
curl -u "api:$MG_SENDING_KEY" \
  https://api.mailgun.net/v3/example.com/messages \
  -F from="agent@example.com" -F to="x@y.com" \
  -F subject="hi" -F text="."
```

## Docs

- [Domain keys](https://documentation.mailgun.com/docs/mailgun/api-reference/send/mailgun/domain-keys)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
