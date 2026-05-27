---
name: OpenAI Agents SDK
slug: openai-agents-sdk
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-27
maintainer: openai
related: []
---

# OpenAI Agents SDK

The Python SDK lazy-reads `OPENAI_API_KEY` on the first `Runner` call. Beyond the OpenAI key itself, third-party tool credentials are entirely on the caller.

## Default mechanism

- `OPENAI_API_KEY` env var (lazy-read on first `Runner` call).
- `set_default_openai_key()`, `set_default_openai_client()`, `set_tracing_export_api_key()` for runtime injection.

## Injection surface

- The `function_tool` decorator does not provide a credential surface. Tools `os.environ` whatever they need.

## Notes

Ad hoc beyond the OpenAI key. For agents that call Stripe, GitHub, or other services, wrap tool functions in a credential broker (Authsome, Infisical Agent Vault, onecli) rather than relying on `os.environ` inside the tool.

## Docs

- [Config](https://openai.github.io/openai-agents-python/config/)
- [DeepWiki: API keys and authentication](https://deepwiki.com/openai/openai-agents-python/13.2-api-keys-and-authentication)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
