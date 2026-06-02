---
name: snyk agent-scan
slug: snyk-agent-scan
type: product
license: unknown
stars: 2513
last_verified: 2026-05-28
maintainer: snyk
related: ["skill-supply-chain","secret-redaction"]
---

# snyk agent-scan

snyk agent-scan is a security scanner aimed at AI agents, MCP servers, and agent skills. It inspects project files, tool definitions, and runtime configuration for credential disclosure surfaces and risky tool shapes before deploy. The tool sits in the same family as Snyk's existing code and dependency scanners, but the rules and heuristics are tuned for agent-shaped artifacts rather than generic application code.

## Architecture

The scanner runs as a CLI and a CI step. It parses MCP server manifests, skill metadata, and tool schemas, then matches them against a ruleset covering secret-shaped literals, overbroad scopes, unsafe shell or filesystem tool definitions, and prompts that echo environment variables. Findings are emitted as SARIF for IDE and PR surfacing. Rule packs ship in the binary, with optional remote refresh against Snyk's vulnerability database for known-bad skill and MCP package hashes.

## Who it is for

Security teams reviewing internal agent deployments, and platform owners who ship agent skills or MCP servers to other teams. It also fits solo developers who want a pre-commit gate before publishing a public skill or MCP package to a registry.

## Trade-offs

It is a static scanner. It catches shapes and patterns, not runtime behavior, so an agent that fetches a tool definition at runtime, or a skill that pulls secrets from a live vault response, will pass scanning while still leaking at execution time. Pair it with a runtime credential broker for full coverage.

## Links

- Repo: [github.com/snyk/agent-scan](https://github.com/snyk/agent-scan)
- Stars: 2513
- License: unknown

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
