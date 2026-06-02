# Changelog

All notable changes to this list are recorded here. Star counts and last-released dates are refreshed monthly; refresh entries are dated and the diff is visible.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [0.3.0] - 2026-05-28

Second gap-research pass. Mined GitHub MCP for MCP gateways, agent-IDP tooling, browser-agent primitives, and OAuth toolkit platforms. Mined the Authsome docs for unlisted service providers and Authsome integration runtimes.

### Added

- 10 new products: agentgateway, Arcade.dev, archestra, Casdoor, Docker MCP Gateway, Kong AI Gateway, metamcp, Microsoft Agent Governance Toolkit, Nango, snyk agent-scan.
- 6 new integrations: browser-use, Crush, LlamaIndex, OpenCode, Plandex, Stagehand.
- 15 new service recipes: Apollo, Atlassian, Buffer, Calendly, Discord, GitLab, Google Workspace, Intercom, Klaviyo, Mailchimp, Microsoft Graph, Postmark, Typeform, X (Twitter), Zapier.
- 2 new patterns: Headless OAuth via device-code flow (RFC 8628), Multiple named connections per provider.
- 3 new threat models: Offline disk-image theft, Process enumeration disclosure, Shell history exposure.

### Pending

- Compatibility matrix entries for the new products (need maintainer confirmation).

## [0.2.0] - 2026-05-27

Gap-research pass. Added entries surfaced by GitHub MCP and Reddit MCP research that the initial subagents missed.

### Added

- 13 new products: AgentGuard, AWS Secrets Manager Agent, Composio, DeepSecure, earl, faramesh-core, hasp, jentic-mini, mcp-governance-sdk, mcp-secrets-plugin, psst, sigcli, zeroid.
- 6 new integrations: AutoGen, Cline, CrewAI, Goose, OpenHands, Pydantic AI.
- 2 new patterns: Non-Human Identity (RFC 8693, SPIFFE), Token substitution proxy.
- 4 new threat models: Browser-agent takeover, Indirect injection through shared data, Over-scoped write credential, Skill and tool supply-chain.

### Changed

- Claude Code integration: documented `.env` reading footgun and `~/.claude/file-history/` plaintext snapshots.
- README: products grid, integrations grid, patterns list, and threat models list updated to reflect new entries.

### Pending

- Compatibility matrix entries for the new products (need maintainer confirmation before publication).

## [0.1.0] - 2026-05-27

### Added

- Initial v1 launch set.
- 15 products: 1Password CLI, Authsome, AWS Secrets Manager, Bitwarden Agent Access, Botiverse agent-vault, Doppler, HashiCorp Vault, Infisical Agent Vault, Keeper Agent Kit, Kontext CLI, LiteLLM Agent Platform, onecli, Pulumi ESC, SOPS, Wirken.
- 11 integrations: Aider, Claude Code, Codex CLI, Continue.dev, Cursor, LangChain, LangGraph, Mastra, OpenAI Agents SDK, Vercel AI SDK, Windsurf.
- 20 service recipes: Anthropic, Cal.com, Cloudflare, GitHub, HubSpot, Linear, Mailgun, Notion, OpenAI, Pinecone, Plaid, Resend, Salesforce, SendGrid, Shopify, Slack, Stripe, Supabase, Twilio, Vercel.
- 12 patterns: agents rule of two, audit trails and SIEM, confused deputy, hook-based injection, just-in-time injection, lethal trifecta, per-task scoping, sandboxed egress, scoped delegation tokens, secret redaction, short-lived tokens, subagent non-inheritance.
- 6 threat models: logging-pipeline leakage, long-running rotation gaps, prompt-injection disclosure, shared-session leakage, subagent inheritance, tool-use credential confusion.
- CATEGORY-MAP.md positioning doc.
- CONTRIBUTING.md with verification gates.

[0.2.0]: https://github.com/agentrhq/awesome-agent-vault
[0.1.0]: https://github.com/agentrhq/awesome-agent-vault
