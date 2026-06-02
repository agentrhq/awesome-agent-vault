---
name: metamcp
slug: metamcp
type: product
license: unknown
stars: 2366
last_verified: 2026-05-28
maintainer: metatool-ai
related: ["hook-based-injection"]
---

# metamcp

metamcp is an MCP aggregator, orchestrator, middleware, and gateway packaged in a single container. It sits in front of multiple MCP servers and exposes them through one endpoint, while handling per-server authentication so downstream tools do not see raw credentials. Agents connect to metamcp instead of connecting to each individual MCP server directly.

## Architecture

The container runs as a long-lived process that fronts a configured set of MCP servers. Inbound MCP traffic from agent clients is routed to the appropriate upstream server based on the tool or namespace being called. Credentials for each upstream server are held in metamcp's own configuration, and the gateway injects them at call time. Middleware hooks let operators rewrite, filter, or log requests and responses, and the orchestrator layer can fan out calls across servers.

## Who it is for

Teams that already run several MCP servers and want one address, one auth surface, and one logging point in front of them. Useful for self-hosted setups where the operator controls both the agents and the MCP servers, and wants to keep per-server tokens out of agent processes.

## Trade-offs

License is currently listed as unknown, which makes it harder to adopt inside organizations with strict OSS review. The single-container model also concentrates blast radius. If metamcp is compromised, every upstream server it fronts is reachable with the credentials it holds.

## Links

- Repo: [github.com/metatool-ai/metamcp](https://github.com/metatool-ai/metamcp)
- Stars: 2366
- License: unknown

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
