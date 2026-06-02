---
name: Docker MCP Gateway
slug: docker-mcp-gateway
type: product
license: Apache-2.0
stars: 1427
last_verified: 2026-05-28
maintainer: docker
related: ["hook-based-injection"]
---

# Docker MCP Gateway

Docker MCP Gateway is the official Docker CLI plugin for running Model Context Protocol servers inside containers. It centralizes how secrets and environment variables are passed to MCP servers, relying on Docker secrets and container isolation instead of writing credentials to shell profiles or agent config files. The gateway sits between an MCP client (Claude Desktop, Cursor, IDE plugins) and the underlying server processes.

## Architecture

The gateway runs as a `docker mcp` CLI subcommand and a long-running gateway process. MCP servers are declared in a catalog file with their image, command, and required secrets. When a client connects, the gateway launches each server inside a container, mounts Docker secrets at runtime, and proxies stdio or SSE traffic back to the client. Secrets are stored in the Docker secret store on the host, never serialized into the MCP server configuration the client sees.

## Who it is for

Developers already running Docker Desktop or Docker Engine who want to consolidate MCP server configuration, isolate untrusted servers from the host filesystem, and avoid pasting raw API keys into per-client JSON config files. Best fit for users running multiple MCP servers across multiple clients.

## Trade-offs

Requires a working Docker daemon and adds container startup latency on each MCP session. Servers must be available as container images or wrapped in a Dockerfile, so quick local Node or Python MCP scripts need an extra packaging step. Non-Docker hosts and minimal CI environments are out of scope.

## Links

- Repo: [github.com/docker/mcp-gateway](https://github.com/docker/mcp-gateway)
- Stars: 1427
- License: Apache-2.0

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
