---
name: Prompt-injection credential disclosure
slug: prompt-injection-exfiltration
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [lethal-trifecta, secret-redaction, hook-based-injection]
---

# Prompt-injection credential disclosure

Untrusted text in the model's context can carry instructions that cause the agent to disclose secrets through whatever channels it has available. The instruction is delivered as data (a support ticket, an email, a document) but read as a directive.

## Surface

Any session that holds credentials in context and also ingests text from outside the trust boundary. The text source is the carrier; the credential surface is the target.

## Worked example

The 2025 Supabase + Cursor incident: a Cursor IDE agent held `service_role` Supabase credentials and read attacker-controlled support tickets. A crafted ticket caused the agent to read private tables and reflect them back. Three patterns from this list each would have closed the vector independently: drop to a read-only role (scoped delegation), enable Supabase MCP's `readonly` flag (rule of two), isolate the credential from sessions ingesting customer text (lethal trifecta).

## Mitigations

- Keep secrets out of model context using placeholders resolved at the tool boundary. See [patterns/hook-based-injection](../patterns/hook-based-injection.md).
- Apply the [Agents Rule of Two](../patterns/agents-rule-of-two.md) to gate which sessions hold which capabilities.
- Sandbox outbound traffic so even a successful instruction has no path to send data outside. See [patterns/sandboxed-egress](../patterns/sandboxed-egress.md).

## Citations

- [General Analysis: Supabase MCP incident](https://generalanalysis.com/blog/supabase-mcp-blog)
- [Simon Willison: The Lethal Trifecta](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
