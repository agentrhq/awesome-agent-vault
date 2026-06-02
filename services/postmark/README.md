---
name: Postmark
slug: postmark
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: postmark
related: [scoped-delegation-tokens]
---

# Postmark

Postmark issues two distinct token classes for its HTTP API. Server tokens are bound to a single Postmark Server, which carries its own sending domain, message stream, and template set. Account tokens authenticate calls against the Account API and can manage servers, domains, signatures, and billing. The two classes use different HTTP headers, so a leaked token of one class cannot be replayed against the other endpoint.

## Credential types

- Server token. Header `X-Postmark-Server-Token`. Scoped to one Server.
- Account token. Header `X-Postmark-Account-Token`. Scoped to the whole account.
- SMTP credentials, derived per Server, for the SMTP relay path.

## Recommended pattern

Provision a dedicated Postmark Server for the agent, then issue a Server token for that Server only. The blast radius of a leak is then a single sending domain and a single message stream, and the token cannot create new servers or rotate signatures.

## Critical scopes to refuse

Account tokens, server creation, domain and signature management, suppression list purges, bounce webhook reconfiguration, template deletion across servers.

## Rotation

Server tokens are rotated from the Server's API Tokens tab, which supports issuing a new token before revoking the old one. Account tokens rotate from Account · API Tokens. Rotate on personnel changes and on any suspected exposure.

## Docs

- [Official docs](https://postmarkapp.com/developer/api/overview)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
