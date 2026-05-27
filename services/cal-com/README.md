---
name: Cal.com
slug: cal-com
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: calcom
related: [short-lived-tokens, scoped-delegation-tokens]
---

# Cal.com

Cal.com's Platform plan ships an OAuth client and managed-user access tokens with a 60-minute lifetime. The short access window is what makes it agent-friendly.

## Credential types

- **Platform OAuth client**: client id + client secret for managed-user provisioning.
- **Managed-user access tokens**: 60m lifetime.
- **Refresh tokens**: 1y lifetime.
- **Personal API keys**: per-user, longer-lived.

## Recommended pattern

Use the Platform OAuth client. Mint managed-user access tokens at task start; refresh hourly. Pass `x-cal-secret-key` when calling provisioning endpoints.

## Critical scopes to refuse

Broad booking or event-type write when read is sufficient. Calendar write when only read is needed.

## Rotation

Access tokens auto-expire at 60m. Refresh tokens last 1y; rotate the client secret on incident.

## Example

```bash
curl -H "Authorization: Bearer $CAL_ACCESS_TOKEN" \
  https://api.cal.com/v2/me
```

## Docs

- [Cal.com API v2](https://cal.com/docs/api-reference/v2/introduction)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
