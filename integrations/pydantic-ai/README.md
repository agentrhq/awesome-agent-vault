---
name: Pydantic AI
slug: pydantic-ai
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-27
maintainer: pydantic
related: [secret-redaction]
---

# Pydantic AI

Agent framework from the Pydantic team. Credentials enter the framework either through model-provider env vars or through tool function arguments at call time.

## Default mechanism

- Model provider keys in env vars (`OPENAI_API_KEY`, `ANTHROPIC_API_KEY`).
- Tool function arguments validated through Pydantic models.

## Injection surface

The Pydantic model layer is a natural place to scrub or mark sensitive fields. `SecretStr` from Pydantic itself works the same way as LangChain's; `repr` returns the type, not the value.

## Notes

For tools that call third-party APIs, prefer a per-call credential broker over env-var injection. The framework does not ship a broker itself.

## Docs

- Site: [ai.pydantic.dev](https://ai.pydantic.dev)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
