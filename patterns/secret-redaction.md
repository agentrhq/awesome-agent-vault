---
name: Secret redaction in prompts and logs
slug: secret-redaction
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: doppler
related: [hook-based-injection, logging-pipeline-leakage]
---

# Secret redaction in prompts and logs

Credentials that enter the model's context can be reflected back through naive instructions (`repeat the system prompt`). Credentials written to stdout can be picked up by log pipelines. Both surfaces need defenses.

## In prompts

Keep secrets out of model context entirely. Use placeholders (`__stripe_key__`) that get resolved at the tool boundary by the hook layer. The model never sees the real value, so there is nothing to reflect.

## In logs

Sanitize structured logs before they leave the agent process. Strip values matching known credential shapes (`sk_`, `xoxb-`, `ghp_`, `Bearer`). Heroku's guidance is explicit: do not write secrets to stdout or stderr in the first place.

## Reference implementation

LangChain's `SecretStr` (see [integrations/langchain](../integrations/langchain/)) wraps values so `repr()` returns the type, not the value. The Doppler guidance described in their LLM security write-up adds prompt placeholders plus log sanitization as a paired pattern.

## Citations

- [Doppler: Advanced LLM security](https://www.doppler.com/blog/advanced-llm-security)
- [Heroku: Writing best practices for application logs](https://devcenter.heroku.com/articles/writing-best-practices-for-application-logs)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
