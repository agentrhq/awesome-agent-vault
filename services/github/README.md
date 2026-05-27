---
name: GitHub
slug: github
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: github
related: [scoped-delegation-tokens, short-lived-tokens]
---

# GitHub

GitHub is the canonical reference for short-lived, repo-scoped agent credentials. A [GitHub App installation token](https://docs.github.com/en/apps/creating-github-apps/authenticating-with-a-github-app/authenticating-as-a-github-app-installation) expires in one hour and can be restricted to a specific subset of repos within an installation.

## Credential types

- **GitHub App installation tokens**: 1h, per-installation, can be scoped to a subset of repos. The right default for agents.
- **Fine-grained PATs**: per-repo permissions, mandatory expiry (max 1y, recommend 90d).
- **Classic PATs**: org-wide scopes. Do not hand to an agent.
- **OAuth user tokens**: for "act on behalf of a user" flows.

## Recommended pattern

Provision a GitHub App, install it on the target org or repo set, and have the agent request an installation token at the start of each task. The token expires before the task finishes long-running work.

## Critical scopes to refuse

`contents:write`, `workflows:write`, `actions:write`, `admin:org`, `secrets:write`, `packages:write`, `delete_repo`. Default to `metadata:read` and add only what the task needs.

## Rotation

Installation tokens self-expire at 1h. Fine-grained PATs require expiry on creation; GitHub auto-expires unused PATs at 1y.

## Example

```bash
# Mint installation token from a GitHub App
gh api /app/installations/$INSTALLATION_ID/access_tokens \
  --method POST \
  --field "repositories[]=repo-a" --field "repositories[]=repo-b" \
  --field "permissions[contents]=read" --field "permissions[issues]=write"
```

## Docs

- [Authenticating as a GitHub App installation](https://docs.github.com/en/apps/creating-github-apps/authenticating-with-a-github-app/authenticating-as-a-github-app-installation)
- [Managing personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
