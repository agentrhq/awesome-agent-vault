---
name: archestra
slug: archestra
type: product
license: unknown
stars: 3765
last_verified: 2026-05-28
maintainer: archestra-ai
related: ["audit-trails-siem"]
---

# archestra

archestra is an enterprise AI platform that combines guardrails with an MCP registry, a gateway, and an orchestrator. It centralizes credential management across a fleet of MCP servers, so that agents and applications can reach external tools through one controlled path. The platform aims to give operations and security teams a single place to register, route, and govern tool access for AI workloads.

## Architecture

The system is built around three coordinated layers. A registry catalogs available MCP servers and their metadata. A gateway sits in front of those servers, terminating agent traffic, injecting credentials, and applying guardrails on inputs and outputs. An orchestrator coordinates multi-step workflows across registered tools. Credentials are held centrally rather than embedded in agent code, and policy decisions, including allow lists and request shaping, are enforced at the gateway boundary before requests leave the platform.

## Who it is for

archestra targets enterprise platform teams that already run, or plan to run, multiple MCP servers internally and need consistent credential handling, routing, and policy enforcement across them. It fits organizations where security, audit, and operations stakeholders need shared control over how agents reach third-party APIs.

## Trade-offs

The platform adds a central gateway and orchestrator to the request path, which becomes a dependency for every agent call. Teams that want a minimal local setup, or that only run a single MCP server, will find the registry, gateway, and orchestrator layers heavier than needed. License terms are not clearly stated, which can complicate procurement and self-hosting decisions.

## Links

- Repo: [github.com/archestra-ai/archestra](https://github.com/archestra-ai/archestra)
- Stars: 3765
- License: unknown

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
