---
name: Notion
slug: notion
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: notion
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Notion

Notion offers internal integration tokens (workspace-static) and public OAuth integrations (rotating). For agents, prefer the public OAuth integration: per-user page grants are explicit and revocable.

## Credential types

- **Public OAuth integration**: access token + refresh token. The refresh response rotates both tokens.
- **Internal integration token**: long-lived, workspace-static. Convenient, but every agent shares the same token.
- **Personal access tokens**: per-user, for scripts.

## Recommended pattern

Use a public OAuth integration so each user explicitly grants access to specific pages. The integration sees only what was shared with it, which gives users a natural permissioning surface and keeps the agent's reach minimal.

## Critical scopes to refuse

`update_content` and `insert_content` capabilities when the task is read-only. Page and database write capabilities unless required.

## Rotation

The refresh response rotates the token pair. Rotate internal integration tokens manually on owner change.

## Example

```bash
curl -H "Authorization: Bearer $NOTION_TOKEN" \
  -H "Notion-Version: 2022-06-28" \
  https://api.notion.com/v1/users/me
```

## Docs

- [Notion authorization](https://developers.notion.com/docs/authorization)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
