---
name: Confused deputy across subagents
slug: confused-deputy
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: sans
related: [subagent-non-inheritance, audit-trails-siem]
---

# Confused deputy across subagents

When a high-privilege agent accepts natural-language instructions from a lower-privilege agent (or from tool output it treats as trusted), the lower-privilege actor effectively inherits the parent's credentials by proxy. The classic "confused deputy" problem from cloud security, reshaped for the multi-agent era.

## Mechanics

A summarizer subagent reads a document and asks the parent to "delete record 42". The parent has delete capability; the summarizer does not. The parent obeys, and the summarizer has just performed a delete it could not perform directly. The deputy was confused about whose authority it was acting under.

## Defensive posture

Authenticate the requesting agent identity at each privilege boundary rather than implicitly trusting the caller. A credential broker that issues per-request capabilities, scoped to the requesting agent rather than the executor, prevents the upward delegation.

## Reference implementation

The SANS framing is the clearest public write-up. The proposed mitigation is a credential broker that asks "who is asking" before issuing rather than letting the executor's identity stand in for the requester's.

## Citation

- [SANS: AI agent as a confused deputy](https://www.sans.org/blog/your-ai-agent-easily-confused-deputy-why-cloud-security-needs-credential-broker)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
