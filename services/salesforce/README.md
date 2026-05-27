---
name: Salesforce
slug: salesforce
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: salesforce
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Salesforce

Salesforce Connected Apps (and the new External Client Apps) support several OAuth flows. For agents, JWT Bearer is the cleanest: no refresh token, no password, just a signed assertion per session.

## Credential types

- **Web Server OAuth**: interactive user flow.
- **JWT Bearer (server-to-server)**: signed assertion, no refresh token.
- **Device flow**: for headless devices.
- **Username-Password flow**: deprecated.

## Recommended pattern

JWT Bearer with a per-agent certificate and the minimum scope set. By May 11, 2026 mandatory External Client App controls apply; plan migration accordingly.

## Critical scopes to refuse

`full`, `refresh_token`, `web`, broad `api` when `chatter_api` or an object-specific scope suffices.

## Rotation

JWT Bearer has no refresh token. Rotate the signing certificate on schedule. For refresh-token flows, enable refresh token rotation (RTR) so each refresh rotates the token pair.

## Example

```bash
# JWT Bearer: sign the assertion, then exchange for an access token
curl https://login.salesforce.com/services/oauth2/token \
  -d grant_type=urn:ietf:params:oauth:grant-type:jwt-bearer \
  -d assertion=$JWT
```

## Docs

- [JWT Bearer flow](https://help.salesforce.com/s/articleView?id=sf.remoteaccess_oauth_jwt_flow.htm)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
