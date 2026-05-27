---
name: Pinecone
slug: pinecone
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: pinecone
related: [scoped-delegation-tokens]
---

# Pinecone

Pinecone API keys are project-scoped. Granular roles (ProjectEditor, ProjectViewer) require the Standard plan or higher; on Starter and Builder the only available role is "All".

## Credential types

- **Project-scoped API keys**: per-project, with a role on Standard+ plans.

## Recommended pattern

One API key per project with the narrowest role the plan supports. On Standard+, use `ProjectViewer` for read-only agents and `ProjectEditor` only when index writes are required. On Starter/Builder, accept the coarse scope and design the agent's reach accordingly.

## Critical scopes to refuse

"All" permission on production indexes when read suffices. On Standard+, write on production indexes when read is sufficient.

## Rotation

Manual key rotation per project. Deletion is immediate and breaks every client using the key. Plan a rolling key swap.

## Example

```bash
curl https://controller.us-east-1.aws.pinecone.io/databases \
  -H "Api-Key: $PINECONE_API_KEY"
```

## Docs

- [Manage API keys](https://docs.pinecone.io/guides/projects/manage-api-keys)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
