---
name: Per-task credential scoping
slug: per-task-scoping
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: authsome
related: [scoped-delegation-tokens, just-in-time-injection]
---

# Per-task credential scoping

Each agent task gets one narrow credential, valid only for the scope of that task, and revoked or expired on completion. Two tasks of the same type get two different credentials. The blast radius is bounded by the task definition.

## Mechanics

A task descriptor names the services, resources, and verbs needed. The broker mints a credential that matches the descriptor, hands it to the agent for the duration of the task, and revokes it on completion. If the descriptor changes, the credential changes.

This shifts the credential conversation from "what does this agent need across all its work" to "what does this task need," which is far narrower in practice.

## Reference implementation

Authsome ([products/authsome](../products/authsome/)) is the reference here. Each `authsome run <command>` provisions task-scoped credentials from the local vault and tears them down on exit; agents read placeholder values and never see the real secret. The pattern works because the proxy layer can mint a fresh delegation per task without the agent participating.

## Citation

- [Authsome documentation](https://authsome.ai)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
