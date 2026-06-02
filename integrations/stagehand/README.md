---
name: Stagehand
slug: stagehand
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-28
maintainer: browserbase
related: ["browser-agent-takeover"]
---

# Stagehand

Stagehand is a browser automation SDK from Browserbase that exposes `act`, `extract`, and `observe` primitives on top of Playwright. Agents written with Stagehand drive a real browser session, so credential handling splits into two layers: provider API keys for the model and LLM calls, and per-site credentials that the browser submits inside login forms.

## Default mechanism

- Provider keys read from environment variables (`OPENAI_API_KEY`, `ANTHROPIC_API_KEY`) at `Stagehand` constructor time.
- `BROWSERBASE_API_KEY` and `BROWSERBASE_PROJECT_ID` env vars when running against managed sessions; local mode bypasses these.
- Per-site credentials passed by the agent author into `page.act()` prompts or typed via `page.fill()`. No built-in secret manager.
- `.env` loading via `dotenv` is left to the host project; Stagehand does not opinion on dotfile location.

## Injection surface

A vault product wraps the Stagehand process so model-provider env vars are populated at spawn and never written to disk. For per-site logins, the cleaner surface is the Browserbase context API: provision an isolated session, inject cookies or run a scripted login step inside a wrapper around `page.act()`, and discard the context on exit. Alternatively, intercept `page.fill()` calls and resolve placeholder tokens to secrets at runtime.

## Notes

Pair Stagehand with Browserbase Contexts when the agent needs to log into third-party sites. Contexts give each task its own cookie jar, which keeps credentials out of the agent transcript and lets the vault scope a credential to a single session id.

## Docs

- Repo: [github.com/browserbase/stagehand](https://github.com/browserbase/stagehand)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
