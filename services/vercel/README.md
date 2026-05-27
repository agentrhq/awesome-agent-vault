---
name: Vercel
slug: vercel
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: vercel
related: [scoped-delegation-tokens]
---

# Vercel

Vercel PATs are scoped to either a user or a team, and an explicit expiry is required for new tokens. The lack of project-level scoping means token holders see the whole team's projects.

## Credential types

- **Personal access tokens (PATs)**: scoped to user or team; explicit expiry required.
- **Deploy hooks**: URL-based trigger; no scope beyond "this deploy".
- **OAuth integrations**: for marketplace apps.

## Recommended pattern

One team-scoped PAT per agent with an explicit expiry. Do not select "No Expiration". Treat the PAT as covering the whole team and design the agent's reach accordingly.

## Critical scopes to refuse

Account-wide tokens, tokens scoped to a user when a team scope is sufficient, no-expiration tokens.

## Rotation

Set an expiry at creation. Rotate per agent task.

## Example

```bash
curl -H "Authorization: Bearer $VERCEL_TOKEN" \
  https://api.vercel.com/v9/projects?teamId=team_X
```

## Docs

- [Vercel scopes and permissions](https://vercel.com/docs/sign-in-with-vercel/scopes-and-permissions)
- [REST API reference](https://vercel.com/docs/rest-api/reference/welcome)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
