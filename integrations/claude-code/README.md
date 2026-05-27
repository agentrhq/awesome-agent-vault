---
name: Claude Code
slug: claude-code
type: integration
license: proprietary
stars: n/a
last_verified: 2026-05-27
maintainer: anthropic
related: [hook-based-injection, sandboxed-egress, subagent-non-inheritance]
---

# Claude Code

Anthropic's CLI coding agent. The credential surface is broader than any other agent on this list: `settings.json` env, MCP server config, pre and post tool-use hooks, and skills. Each surface has a different blast radius.

## Default mechanism

- `settings.json` `env` block plus OS environment variables.
- `permissions.deny` blocks `.env` reads.
- MCP server config stores tokens in plaintext under `mcpServers[*].env`.

## Injection surface

- **Hooks**: pre and post tool-use hooks can intercept tool calls. HTTP hooks restrict environment interpolation through `allowedEnvVars`.
- **Skills**: skills can wrap shell calls; the `agent-vault-http` and `agent-vault-cli` skills wrap Infisical Agent Vault's proxy and CLI.
- **MCP**: each MCP server has an `env` map.

## Best community example

[Infisical Agent Vault](../../products/infisical-agent-vault/) on port 14322. Placeholder tokens (`__anthropic_api_key__`, `__github_pat__`) are swapped for real ones server-side, so the agent process never holds raw credentials.

## Known footguns

- Claude Code reads `.env` files even with `permissions.deny` on `.env*` paths in some configurations, and writes file-snapshot history to `~/.claude/file-history/` in plaintext. Community discussions document the gap on [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1lgudw2/) and [r/SideProject](https://www.reddit.com/r/SideProject/comments/1rec44l/). Prefer keeping secrets out of `.env` entirely (resolve via a broker or `op run`) rather than relying on deny rules alone.
- `.mcp.json` is unsuitable for committing secrets: env-var expansion has known issues (#9427) and org-managed plugins cannot accept user input.

## Notes

The Anthropic engineering blog post "Securely deploying AI agents" recommends vault-mediated credentials over plaintext env. The sandbox sits on Linux bubblewrap and macOS seatbelt, with outbound traffic going through a domain-allowlisted egress proxy.

## Docs

- [Claude Code settings](https://code.claude.com/docs/en/settings)
- [Hooks complete guide](https://claudefa.st/blog/tools/hooks/hooks-guide)
- [Securely deploying AI agents](https://code.claude.com/docs/en/agent-sdk/secure-deployment)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
