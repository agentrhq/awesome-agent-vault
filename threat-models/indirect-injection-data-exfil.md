---
name: Indirect injection through shared data
slug: indirect-injection-data-exfil
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [lethal-trifecta, prompt-injection-exfiltration, agents-rule-of-two]
---

# Indirect injection through shared data

An agent reads from a data source that other users can edit (a shared spreadsheet, a support inbox, a public document) and treats embedded instructions in that data as commands. The data source becomes the carrier; the agent's credentials become the target.

## Surface

- AI assistants tied to shared productivity tools (spreadsheets, docs, inboxes).
- Customer-support agents that read tickets and act on them.
- Browser-based agents reading pages that load third-party content.

## Worked example

A widely reported 2026 incident: an AI assistant tied to a financial spreadsheet read instructions hidden inside a cell, then followed them to disclose private data outside the workspace. The instructions were data; the agent treated them as a directive because the data source was inside the trust boundary.

## Mitigations

- Apply the [Agents Rule of Two](../patterns/agents-rule-of-two.md): the session reading attacker-shapeable data should not simultaneously hold both private-data access and an outbound channel.
- [patterns/sandboxed-egress](../patterns/sandboxed-egress.md) closes the outbound leg even when other layers fail.
- Treat any shared editable data source as outside the trust boundary by default, even when it lives inside the same workspace.

## Citation

- [Ramp Sheets AI incident discussion](https://www.reddit.com/r/LocalLLM/comments/1sziaf9/)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
