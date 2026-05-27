---
name: Audit trails and SIEM integration
slug: audit-trails-siem
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: microsoft
related: [confused-deputy, per-task-scoping]
---

# Audit trails and SIEM integration

Every tool call attributes to a specific non-human identity, the human delegator behind it, and a credential reference ID rather than the credential value. The logs feed into a SIEM where volume, scope, timing, and attribution-chain anomalies are detected the same way they are for human accounts.

## Mechanics

Three identifiers per call: agent identity, human delegator, credential reference. Never the secret value, never just "an agent did this". The SIEM compares the chain against a baseline; spikes in scope, unusual timing, or sudden breadth in the resources touched are surfaced as signals.

Without per-agent identity, an oncall responder cannot distinguish a runaway agent from its operator. They cannot revoke the right credential without revoking the human's access too.

## Reference implementation

Microsoft Entra Agent ID treats each agent as a first-class principal. Sign-in and audit logs pipe directly to SIEM with the agent's identity in the actor field. Wirken ([products/wirken](../products/wirken/)) provides a lighter, single-binary version with a hash-chained log for small operators.

## Citation

- [Microsoft Entra Agent ID logs](https://learn.microsoft.com/en-us/entra/agent-id/sign-in-audit-logs-agents)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
