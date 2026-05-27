---
name: LangGraph
slug: langgraph
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-27
maintainer: langchain-ai
related: [per-task-scoping, secret-redaction]
---

# LangGraph

LangGraph is the only framework on this list with a documented "fetch user credentials from a secret store, never put them in graph state" rule.

## Default mechanism

- `langgraph.json` `auth` block.
- Secrets accessed via `RunnableConfig["configurable"]`.
- LangSmith workspace-saved secrets in the Playground.

## Injection surface

- The `Auth` handler populates `config["configurable"]["langgraph_auth_user"]` and can pull per-request secrets from any backend.
- `disable_studio_auth: "true"` locks Studio out of production deployments.

## Best community example

The [Custom Authentication launch post](https://blog.langchain.com/custom-authentication-and-access-control-in-langgraph/) shows fetching per-user OAuth tokens at request time so the graph never persists them.

## Docs

- [Custom authentication](https://docs.langchain.com/langgraph-platform/custom-auth)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
