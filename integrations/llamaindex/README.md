---
name: LlamaIndex
slug: llamaindex
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-28
maintainer: run-llama
related: ["scoped-delegation-tokens"]
---

# LlamaIndex

LlamaIndex is a data framework for LLM applications. It provides data loaders, indexes, retrievers, and tool abstractions that connect models to external sources. Credentials are carried by individual readers and tool spec packages rather than by a central broker, so secret handling follows whatever pattern each loader adopts.

## Default mechanism

- Environment variables read directly inside reader and tool modules (for example `OPENAI_API_KEY`, `NOTION_INTEGRATION_TOKEN`, `SLACK_BOT_TOKEN`).
- Constructor arguments passed to `LlamaHub` readers and `ToolSpec` classes, often forwarded into third-party SDK clients.
- `.env` files loaded via `python-dotenv` in user code, not by the framework itself.
- For OAuth-backed sources, a long-lived token is typically generated out of band and pasted into env or config.

## Injection surface

A vault product can wrap reader and tool initialization. Two clean surfaces exist. First, environment injection at process start, since most readers fall back to `os.environ`. Second, a thin factory layer that constructs `BaseReader` or `BaseToolSpec` instances with credentials resolved at call time, leaving the framework code untouched. Per-tool scoping is feasible because each reader and tool spec is a separate object with its own auth boundary.

## Notes

LlamaIndex does not ship an auth broker, so credentials inherit the lifetime of the host process. Common pairing with Composio handles OAuth flows for sources like Gmail, Notion, and Slack, exchanging user tokens for short-lived access tokens before they reach the reader. Outside Composio, treat each `ToolSpec` as a credential boundary and rotate keys on the source side.

## Docs

- Repo: [github.com/run-llama/llama_index](https://github.com/run-llama/llama_index)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
