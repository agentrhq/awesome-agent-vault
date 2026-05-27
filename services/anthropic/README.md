---
name: Anthropic
slug: anthropic
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: anthropic
related: [scoped-delegation-tokens]
---

# Anthropic

Anthropic ships Workspace API keys (full or read-only per workspace) and separate Admin API keys for org operations. Treat the two as different trust domains.

## Credential types

- **Workspace API keys**: per-workspace, full or read-only.
- **Admin API keys**: org-wide member, invite, billing operations.
- **Organization-level keys**: provisioning and audit operations.

## Recommended pattern

One Workspace key per environment with read-only where possible. Admin keys never share a vault with inference keys. Production inference workspaces hold no Admin keys at all.

## Critical scopes to refuse

Admin scope (org, member, invite). `workspace:billing`. Write on production workspaces unless required.

## Rotation

Rotate workspace keys on developer offboarding. Admin keys live in a separate secret store with a stricter cadence.

## Example

```bash
curl https://api.anthropic.com/v1/messages \
  -H "x-api-key: sk-ant-..." \
  -H "anthropic-version: 2023-06-01" \
  -d '{"model":"claude-opus-4-7","max_tokens":1,"messages":[{"role":"user","content":"hi"}]}'
```

## Docs

- [Workspaces](https://platform.claude.com/docs/en/build-with-claude/workspaces)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
