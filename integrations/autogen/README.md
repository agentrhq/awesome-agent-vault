---
name: AutoGen
slug: autogen
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-27
maintainer: microsoft
related: [subagent-non-inheritance]
---

# AutoGen

Microsoft's multi-agent orchestration framework. Credentials flow through `model_client_config` and tool registration. Multi-agent conversations inherit credentials from the conductor process unless explicitly partitioned.

## Default mechanism

- Model client config carries provider keys.
- Tool functions read credentials from `os.environ` at call time.

## Injection surface

The conductor pattern means every spawned agent inherits the parent's env by default. Use Microsoft Entra Agent ID for per-agent identity in production deployments; the credential surface follows the identity.

## Notes

Apply [patterns/subagent-non-inheritance](../../patterns/subagent-non-inheritance.md) carefully. The default inheritance behavior is convenient and wide; agent-class roles deserve different credentials.

## Docs

- Repo: [github.com/microsoft/autogen](https://github.com/microsoft/autogen)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
