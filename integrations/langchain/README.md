---
name: LangChain
slug: langchain
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-27
maintainer: langchain-ai
related: [secret-redaction]
---

# LangChain

LangChain ships `SecretStr` and `secret_from_env`, the most thoughtful in-code credential primitive on this list. Wrapping a value in `SecretStr` keeps it out of `repr()` and logs by default.

## Default mechanism

- `os.environ` plus `python-dotenv`.
- `langchain_core.utils.secret_from_env` reads an env var and returns a `SecretStr`.
- Component constructors auto-read `*_API_KEY`.

## Injection surface

- `RunnableConfig["configurable"]` for runtime or per-user secrets.
- The deepagents production guide recommends fetching from Vault or AWS Secrets Manager at request time, not boot time.

## Best community example

The [production deployment guide](https://docs.langchain.com/oss/python/deepagents/going-to-production) uses Vault plus `secret_from_env` so every secret in memory is a `SecretStr` that scrubs logs.

## Docs

- [`secret_from_env` reference](https://python.langchain.com/api_reference/core/utils/langchain_core.utils.utils.secret_from_env.html)
- [Going to production](https://docs.langchain.com/oss/python/deepagents/going-to-production)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
