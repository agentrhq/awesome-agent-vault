---
name: Logging-pipeline secret leakage
slug: logging-pipeline-leakage
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: heroku
related: [secret-redaction, audit-trails-siem]
---

# Logging-pipeline secret leakage

Credentials written to stdout or stderr by the agent process get picked up by the logging pipeline, fanned out to observability backends, indexed for full-text search, and surfaced months later in a query. The credential itself may have rotated; the log record has not.

## Surface

- Agent debug logging that prints request and response bodies verbatim.
- Structured loggers that serialize the full request including `Authorization` headers.
- Test failures that dump environment variables to CI output.
- Stack traces that include the value of a `SecretStr` because something downstream called `str()` on it.

## Mitigations

- Do not write secrets to stdout or stderr in the first place (Heroku's explicit guidance).
- Sanitize structured logs at the agent process boundary. Strip values matching known credential shapes.
- Wrap values in a type that scrubs on `repr`/`str` so accidental string conversion fails closed. LangChain's `SecretStr` is the reference here.
- Apply [patterns/secret-redaction](../patterns/secret-redaction.md) as a paired prompt-and-log policy.

## Citation

- [Heroku: Writing best practices for application logs](https://devcenter.heroku.com/articles/writing-best-practices-for-application-logs)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
