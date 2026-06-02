---
name: Apollo
slug: apollo
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: apollo
related: [scoped-delegation-tokens]
---

# Apollo

Apollo authenticates API calls with per-user API keys generated from the Apollo dashboard. Keys carry the full permissions of the issuing user and are not scoped per resource, list, or sequence. An agent holding a key can read and modify any contact, account, or sequence the user can access, so isolation has to happen at the agent and key level.

## Credential types

- Master API key (account-wide, full user permissions)
- Per-user API keys generated in the Apollo settings panel
- OAuth is not generally available for third-party agents on the standard plans

## Recommended pattern

Provision a dedicated Apollo seat for the agent, generate a key bound to that seat, and inject it through a vault at request time. Do not reuse a human teammate's key. Pair the key with outbound allow-listing and a per-agent rate cap to contain blast radius, since the API itself does not expose finer scopes.

## Critical scopes to refuse

Bulk export of contacts and accounts, deletion of sequences or saved searches, sending emails on behalf of a real user mailbox, modifying billing or team membership, granting new API keys.

## Rotation

Rotate at least every 90 days, and immediately on agent decommission or suspected leak. Rotation is manual: revoke the old key in the Apollo settings and reissue, then update the vault entry.

## Docs

- [Official docs](https://docs.apollo.io/reference/authentication)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
