---
name: Discord
slug: discord
type: service
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: discord
related: [scoped-delegation-tokens]
---

# Discord

Discord exposes two distinct credential models. Bot tokens authenticate an application as a bot user inside guilds, while OAuth 2.0 authorization codes and access tokens authenticate on behalf of a Discord user. The two flows grant different permission surfaces and have different revocation paths, so the choice of credential shapes what an agent can do and who is accountable for the action.

## Credential types

- Bot tokens (long-lived, tied to the application, scoped by guild permissions and gateway intents)
- OAuth 2.0 access tokens (user-context, scoped via the `scope` parameter, refreshable)
- OAuth 2.0 refresh tokens (long-lived, used to mint new access tokens)
- Client credentials grant tokens (application-only, for application-owned resources)
- Webhook tokens (per-channel, write-only, no scope granularity)

## Recommended pattern

For agents acting on behalf of a user, use OAuth 2.0 with the authorization code flow and request only the scopes the task requires. Bot tokens should be reserved for genuine bot personas and kept out of agent runtime memory, with the bot's guild permissions and gateway intents trimmed to the minimum.

## Critical scopes to refuse

`bot` with `Administrator` permission, `applications.commands.update`, `guilds.join`, `messages.read` for unrelated guilds, `webhook.incoming` when not authoring webhooks, `email` unless identity is required.

## Rotation

Bot tokens can be regenerated from the Developer Portal, which invalidates the previous token immediately. OAuth access tokens expire (typically 7 days) and rotate via the refresh token grant. Treat any leaked token as compromised and regenerate.

## Docs

- [Official docs](https://discord.com/developers/docs/topics/oauth2)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
