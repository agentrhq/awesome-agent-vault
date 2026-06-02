---
name: Crush
slug: crush
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-28
maintainer: charmbracelet
related: [hook-based-injection]
---

# Crush

Charm's terminal AI coding assistant, built with Bubble Tea. The successor project to `opencode-ai/opencode`, which is archived. Supports OpenAI, Anthropic, Google Gemini, AWS Bedrock, Groq, Azure OpenAI, OpenRouter, and more.

## Default mechanism

- `$HOME/.crush.json` (or project-local `.crush.json`) holds provider configuration and references credentials by name.
- Provider env vars (`OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, etc.) read at startup.

## Injection surface

- Provider blocks in the JSON config can reference env vars rather than holding literals, which keeps the config file commitable.
- LSP plus tool execution mean Crush is a privileged tool runner; treat its provider keys as production credentials.

## Notes

For long-running Crush sessions, prefer just-in-time credential injection (see [patterns/just-in-time-injection](../../patterns/just-in-time-injection.md)) over leaving provider keys in the user environment.

## Docs

- Repo: [github.com/charmbracelet/crush](https://github.com/charmbracelet/crush)
- Predecessor (archived): [github.com/opencode-ai/opencode](https://github.com/opencode-ai/opencode)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
