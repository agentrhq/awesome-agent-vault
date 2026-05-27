---
name: OpenAI
slug: openai
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: openai
related: [scoped-delegation-tokens, per-task-scoping]
---

# OpenAI

OpenAI ships per-Project keys and a Restricted Permissions option that lets you choose which endpoints a key can call. Service account keys keep agent identity distinct from human users.

## Credential types

- **User keys**: tied to an individual. Avoid for production agents.
- **Project keys**: scoped to one project.
- **Service account keys**: same scoping, no human identity attached.
- **Restricted keys**: All / Restricted / Read-only on a per-endpoint basis.
- **Admin keys**: org-level. Keep these in a separate vault.

## Recommended pattern

Create one Project per agent (or agent class). Mint a service account key with Restricted permissions on only the endpoints needed (`v1/chat/completions:read`, etc.). Admin keys never co-locate with inference keys.

## Critical scopes to refuse

`api.model.write`, `api.fine_tuning.write`, `api.assistants.write`, `api.files.write`. Any Admin scope.

## Rotation

Rotate project keys on member change. Admin keys live in a separate vault and rotate on a stricter cadence.

## Example

```bash
curl https://api.openai.com/v1/models \
  -H "Authorization: Bearer sk-proj-..."
```

## Docs

- [OpenAI RBAC](https://platform.openai.com/docs/guides/rbac)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
