---
name: Browser-agent takeover
slug: browser-agent-takeover
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [lethal-trifecta, prompt-injection-exfiltration]
---

# Browser-agent takeover

An agent embedded in a browser inherits the user's existing authenticated sessions. A crafted web page can convince the agent to perform actions in those sessions, including reading credentials from password manager extensions that the user has already unlocked.

## Surface

- Agentic browsers that share session state with the user's tabs.
- Browser-based agents with extensions installed by the user.
- Single-sign-on environments where the agent's session covers many downstream services.

## Worked example

A reported 2026 finding: a zero-click prompt-injection vector against an agentic browser allowed a crafted page to direct the agent to retrieve credentials from a connected password-manager extension within the authorized session. The agent had no malicious intent; the page provided the instructions and the agent treated them as legitimate context.

## Mitigations

- Browser-agent sessions should not co-exist with user sessions in the same browser profile. Use a separate, isolated profile per agent.
- Password manager extensions should not auto-unlock for agent-driven tabs.
- The agent's outbound surface should be filtered separately from the user's. See [patterns/sandboxed-egress](../patterns/sandboxed-egress.md).

## Citation

- [Zenity PleaseFix / Perplexity Comet discussion](https://www.reddit.com/r/Perplexity/comments/1rjtcis/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
