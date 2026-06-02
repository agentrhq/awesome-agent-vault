---
name: Microsoft Agent Governance Toolkit
slug: ms-agent-governance
type: product
license: MIT
stars: 3757
last_verified: 2026-05-28
maintainer: microsoft
related: ["non-human-identity","audit-trails-siem"]
---

# Microsoft Agent Governance Toolkit

An open-source toolkit from Microsoft for governing AI agents that need to act on behalf of users or services. It bundles policy enforcement, zero-trust identity primitives, and runtime sandboxing into a single deployable layer. Rather than storing or brokering credentials directly, it provides the scaffolding around them, defining who an agent is, what it may do, and how each call is logged.

## Architecture

The toolkit sits between agent runtimes and the systems they act on. A policy engine evaluates each tool call against signed identity claims, requested scopes, and tenant rules before the call leaves the sandbox. Identity is modeled as a separate principal per agent, distinct from the invoking user, with workload attestation tied to Entra ID or any OIDC issuer. Sandboxing isolates each agent in a constrained execution context, and structured decision logs flow to standard SIEM sinks.

## Who it is for

Platform and security teams at organizations deploying agents into regulated environments, particularly those already standardized on Microsoft Entra, Defender, or Purview. It suits teams that want to assemble their own stack from open components rather than adopt a single vendor agent platform.

## Trade-offs

It is governance scaffolding, not a vault. Operators must still wire in a credential broker, a secrets backend, and per-provider OAuth flows. The opinionated Entra and Azure logging integrations are smooth on Microsoft estates and require adapter work elsewhere.

## Links

- Repo: [github.com/microsoft/agent-governance-toolkit](https://github.com/microsoft/agent-governance-toolkit)
- Stars: 3757
- License: MIT

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
