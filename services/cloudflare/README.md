---
name: Cloudflare
slug: cloudflare
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: cloudflare
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Cloudflare

Cloudflare API tokens (`cfut_`) combine permission groups, resource restrictions, IP filters, and TTL on a single token. That combination is closer to the platonic ideal of an agent credential than most services achieve.

## Credential types

- **API tokens** (`cfut_`): per-permission-group, per-resource, optional IP allowlist, optional TTL.
- **Global API key**: full account access. Do not hand to an agent.

## Recommended pattern

One API token per agent, with one permission group, one resource (zone or account), an IP allowlist, and a TTL. If any one of those four can be tightened further, tighten it.

## Critical scopes to refuse

`Zone:Edit`, `Account:Edit`, `Workers Scripts:Edit`, `DNS:Edit` when read suffices. Never use the Global API Key.

## Rotation

Use TTL on token creation so rotation is automatic. Rotate on incident or member departure.

## Example

```bash
curl -H "Authorization: Bearer $CF_TOKEN" \
  https://api.cloudflare.com/client/v4/zones/$ZONE_ID/dns_records
```

## Docs

- [Create an API token](https://developers.cloudflare.com/fundamentals/api/get-started/create-token/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
