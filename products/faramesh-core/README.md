---
name: faramesh-core
slug: faramesh-core
type: product
license: unknown
stars: 56
last_verified: 2026-05-27
maintainer: faramesh
related: [non-human-identity, audit-trails-siem]
---

# faramesh-core

Governance-as-Code library for agent credential brokering. Policies are declarative; credentials are issued through the broker only when the policy admits the request.

## Architecture

A policy engine sits between agent and credential store. Policies declare which agent identities can request which credentials under which conditions. Audit logs are first-class.

## Who it is for

Teams who like the OPA / Cedar shape and want the same model for agent credentials.

## Trade-offs

Adds a policy language to the stack. Worthwhile only when the credential decisions are non-trivial.

## Links

- Repo: [github.com/faramesh/faramesh-core](https://github.com/faramesh/faramesh-core)
- Last updated: 2026-05-27
- Stars: 56

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
