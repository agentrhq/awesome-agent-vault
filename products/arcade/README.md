---
name: Arcade.dev
slug: arcade
type: product
license: MIT
stars: 911
last_verified: 2026-05-28
maintainer: ArcadeAI
related: ["scoped-delegation-tokens"]
---

# Arcade.dev

Arcade.dev is an MCP server framework paired with a tool development library, distributed as a commercial OAuth-for-agents platform that sits alongside Composio in the same category. It handles per-user OAuth token issuance, refresh, and storage for a catalog of third-party APIs, so an agent can act on behalf of a specific human against services like Gmail, GitHub, Slack, and Notion without the agent holding raw credentials.

## Architecture

Arcade runs as a hosted control plane plus a self-hostable engine. Tools are defined in Python using the arcade-mcp library and surfaced to clients over the Model Context Protocol. When an agent invokes a tool that requires user authorization, the engine returns an OAuth flow URL, captures the resulting tokens in its vault, and from then on injects them at call time. The framework separates tool code, auth provider config, and per-user secrets, so adding a new provider does not require rewriting tool logic.

## Who it is for

Teams building agent products that must call third-party APIs as the end user rather than as the application, and who want a managed token store, consent flow, and tool catalog instead of writing OAuth glue for every provider.

## Trade-offs

The hosted engine is the path of least resistance; the self-hosted option exists but carries operational cost. Provider coverage is broad but uneven, and any provider not in the catalog still needs a custom toolkit. Pricing is per-active-user above the free tier, which can outpace a flat secrets-manager bill at scale.

## Links

- Repo: [github.com/ArcadeAI/arcade-mcp](https://github.com/ArcadeAI/arcade-mcp)
- Stars: 911
- License: MIT

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
