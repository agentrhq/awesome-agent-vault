---
name: Twilio
slug: twilio
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: twilio
related: [scoped-delegation-tokens]
---

# Twilio

Twilio offers Subaccounts that wall off resources, and Restricted API keys that can be limited to a specific resource family (Messages, Voice, Verify, etc.).

## Credential types

- **Account SID + Auth Token**: full account access. Do not hand to an agent.
- **Main API keys**: full account, but rotatable.
- **Standard keys**: account-wide.
- **Restricted keys**: limited to specific resource types.
- **Subaccounts**: walled-off children with their own SID and tokens.

## Recommended pattern

One Subaccount per agent or tenant. Inside the Subaccount, mint a Restricted API key limited to the verbs the agent needs (Messages create only, for example).

## Critical scopes to refuse

`Accounts`, `Keys`, full voice or messaging surface when only one verb is needed.

## Rotation

Rotate restricted keys quarterly. To rotate the Auth Token, promote a new key, then demote the old one.

## Example

```bash
curl -u "AC...:SK..." \
  https://api.twilio.com/2010-04-01/Accounts/AC.../Messages.json \
  -d "From=+1..." -d "To=+1..." -d "Body=hi"
```

## Docs

- [Twilio API keys](https://www.twilio.com/docs/iam/api-keys)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
