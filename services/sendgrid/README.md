---
name: SendGrid
slug: sendgrid
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: twilio
related: [scoped-delegation-tokens]
---

# SendGrid

SendGrid offers Full Access, Custom (Restricted), and Billing Access keys. Only the Custom key offers per-endpoint scoping, which is what makes it agent-suitable.

## Credential types

- **Full Access**: read and write everything. Do not hand to an agent.
- **Custom (Restricted)**: per-endpoint scopes.
- **Billing Access**: isolated billing surface.

## Recommended pattern

One Custom access key per agent with `mail.send` set to Full Access, every other scope set to either Read or No Access. Billing keys live in a separate vault.

## Critical scopes to refuse

`billing`, `api_keys` (which would let the agent mint more keys), `marketing`, `user.account`.

## Rotation

Rotate on owner change. Keep the billing key isolated from sending keys.

## Example

```bash
curl -X POST https://api.sendgrid.com/v3/mail/send \
  -H "Authorization: Bearer SG.xxxx" \
  -H "Content-Type: application/json" \
  -d '{"personalizations":[{"to":[{"email":"x@y.com"}]}],"from":{"email":"agent@example.com"},"subject":"hi","content":[{"type":"text/plain","value":"."}]}'
```

## Docs

- [API keys](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/api-keys)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
