---
name: HubSpot
slug: hubspot
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: hubspot
related: [scoped-delegation-tokens]
---

# HubSpot

HubSpot private apps issue OAuth-backed access tokens with per-CRM-scope grants. Each token is bound to one private app, which makes per-agent scoping natural.

## Credential types

- **Private app access tokens**: OAuth-backed, per-app scopes.
- **Public app OAuth**: for marketplace integrations.

## Recommended pattern

One private app per agent with only the CRM object scopes the task needs. Audit the scope list on each release.

## Critical scopes to refuse

`crm.objects.contacts.write` when read is enough, `crm.export`, `settings.users.write`, automation write.

## Rotation

Rotate every 6 months on a planned cadence. On compromise, immediate or 7-day scheduled rotation.

## Example

```bash
curl https://api.hubapi.com/crm/v3/objects/contacts \
  -H "Authorization: Bearer pat-na1-..."
```

## Docs

- [Private apps](https://developers.hubspot.com/docs/guides/apps/private-apps/overview)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
