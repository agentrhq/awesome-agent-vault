---
name: browser-use
slug: browser-use
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-28
maintainer: browser-use
related: ["browser-agent-takeover"]
---

# browser-use

browser-use is an open-source Python framework that lets an LLM drive a real browser to complete web tasks. It is one of the few agent runtimes that treats credential handling as a first-class concern, with explicit primitives for masking secrets from the model and constraining where those secrets may be sent.

## Default mechanism

- Model API keys (`OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, etc.) read from process environment.
- Per-task credentials passed via the `sensitive_data` argument on the `Agent` constructor, as a dict of placeholder · value pairs.
- Optional `allowed_domains` list scoping which origins a given secret may be typed into.
- Browser state (cookies, localStorage) persisted via Playwright user-data-dir when configured.

## Injection surface

A vault product can populate `sensitive_data` at agent construction time, keeping raw secrets out of the prompt and the trajectory. The model only sees the placeholder token (for example `x_linear_token`); the runtime substitutes the real value when typing into an allowlisted domain. For network-level injection, browser-use also runs under Playwright, so an HTTPS proxy or extension can rewrite outbound requests before the page sees them.

## Notes

The `sensitive_data` + `allowed_domains` pairing is the safer pattern. Passing secrets via plain prompt text defeats the placeholder masking and will leak into logs and screenshots. Common pairing: vault-managed `sensitive_data` for site logins, env vars for the model provider key.

## Docs

- Repo: [github.com/browser-use/browser-use](https://github.com/browser-use/browser-use)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
