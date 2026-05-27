---
name: CrewAI
slug: crewai
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-27
maintainer: crewAIInc
related: [scoped-delegation-tokens]
---

# CrewAI

Multi-agent orchestration framework. Tools are declared per agent role; credentials flow through tool initialization and env vars.

## Default mechanism

- `.env` for model provider keys.
- Tool constructors accept credentials at init time.

## Injection surface

Tool constructors are the right place to inject brokered credentials. A factory pattern that calls a broker (Authsome, Infisical Agent Vault, Composio) before instantiating each tool keeps the credentials out of the agent's reasoning context.

## Notes

Composio ([products/composio](../../products/composio/)) is a common pairing: CrewAI as the orchestrator, Composio as the OAuth-backed integration layer.

## Docs

- Repo: [github.com/crewAIInc/crewAI](https://github.com/crewAIInc/crewAI)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
