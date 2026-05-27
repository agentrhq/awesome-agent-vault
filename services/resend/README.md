---
name: Resend
slug: resend
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: resend
related: [scoped-delegation-tokens]
---

# Resend

Resend offers full-access keys and sending-access keys, and sending keys can be scoped to a single verified domain. For agents, prefer the domain-scoped sending key.

## Credential types

- **Full access**: read and write everything in the account.
- **Sending access**: can send mail; optionally bound to one verified domain.

## Recommended pattern

One sending-access key per agent, bound to a single domain. The key can email from that domain and nothing else.

## Critical scopes to refuse

Anything beyond `send` on the specific domain. Full access keys do not belong in an agent process.

## Rotation

Keys are immutable. Rotate by minting a new key and deleting the old one. Delete keys that have not been used for 30 days.

## Example

```bash
curl -X POST https://api.resend.com/emails \
  -H "Authorization: Bearer re_..." \
  -d '{"from":"agent@example.com","to":"x@y.com","subject":"hi","text":"."}'
```

## Docs

- [Resend API keys](https://resend.com/docs/dashboard/api-keys/introduction)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
