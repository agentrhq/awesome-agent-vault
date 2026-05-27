# Awesome Agent Vault [![Awesome](https://awesome.re/badge.svg)](https://github.com/sindresorhus/awesome)

> The category map for giving agents credentials safely. Products, integrations, per-service recipes, patterns, threat models. Neutral, curated, no CTAs.

This list is a directory, not a product. `agent-vault` is also the name of a product shipped by Infisical, listed below alongside every other entry in this space. See [CATEGORY-MAP.md](CATEGORY-MAP.md) for how this list stays neutral.

Last verified: 2026-05-27.

## Contents

- [The category map](#the-category-map)
- [Compatibility matrix](#compatibility-matrix)
- [Products](#products)
- [Integrations](#integrations)
- [Services](#services)
- [Patterns](#patterns)
- [Threat models](#threat-models)
- [Contributing](#contributing)
- [License](#license)

## The category map

Five reader-intent buckets. Every entry belongs to exactly one bucket.

```text
                  Awesome Agent Vault
                          |
   +--------+----------+--+----+----------+-------------+
   |        |          |      |          |             |
Products  Integr-   Services  Patterns  Threat models  Web
          ations    (recipes) (the IP)  (security)     (matrix)
```

- **Products** are the things you install or call: vaults, proxies, identity layers, credential gateways.
- **Integrations** are the agent platforms that consume those products: Claude Code, Codex, Cursor, LangChain, etc.
- **Services** are per-third-party-API recipes: Stripe, GitHub, Slack. Each names the credential type to mint and the scopes to refuse.
- **Patterns** are named recipes for recurring problems, each citing the project that demonstrably handles it best.
- **Threat models** are documented attack surfaces with mitigations and references.

## Compatibility matrix

Rows are products. Columns are agent platforms. Cells use a closed vocabulary: yes / partial / no / unknown. Footnotes carry nuance.

| Product | Claude Code | Codex CLI | Cursor | Aider | Windsurf | LangChain | OpenAI Agents SDK | Mastra | Vercel AI SDK | Continue.dev |
|---|---|---|---|---|---|---|---|---|---|---|
| [1Password CLI](products/1password-cli/) | yes | yes [^op-codex] | partial | yes | partial | yes | yes | yes | yes | yes |
| [Authsome](products/authsome/) | yes | yes | yes | yes | yes | partial | partial | partial | partial | yes |
| [AWS Secrets Manager](products/aws-secrets-manager/) | partial | partial | partial | partial | partial | yes | yes | yes | yes | partial |
| [Bitwarden Agent Access](products/bitwarden-agent-access/) | yes | partial | partial | no | no | partial | partial | no | no | no |
| [Botiverse agent-vault](products/botiverse-agent-vault/) | partial | no | no | no | no | partial | no | no | no | no |
| [Doppler](products/doppler/) | yes | yes | yes | yes | yes | yes | yes | yes | yes | yes |
| [HashiCorp Vault](products/hashicorp-vault/) | partial | partial | partial | partial | partial | yes | yes | yes | yes | partial |
| [Infisical Agent Vault](products/infisical-agent-vault/) | yes | partial | partial | partial | partial | partial | partial | partial | partial | partial |
| [Keeper Agent Kit](products/keeper-agent-kit/) | yes | yes | yes | no | no | no | no | no | no | no |
| [Kontext CLI](products/kontext-cli/) | yes | yes | yes | partial | partial | no | no | no | no | partial |
| [LiteLLM Agent Platform](products/litellm-agent-platform/) | yes | yes | partial | partial | partial | yes | yes | partial | partial | partial |
| [onecli](products/onecli/) | yes | yes | yes | partial | partial | partial | partial | partial | partial | partial |
| [Pulumi ESC](products/pulumi-esc/) | yes | yes | yes | yes | yes | yes | yes | yes | yes | yes |
| [SOPS](products/sops/) | partial | partial | partial | partial | partial | partial | partial | partial | partial | partial |
| [Wirken](products/wirken/) | partial | partial | no | no | no | no | no | no | no | no |

[^op-codex]: 1Password Environments MCP server shipped a Codex-first integration in May 2026.

Cell meanings: **yes** has a maintained adapter or first-party docs. **partial** can be wired in but requires custom glue. **no** has no public path. **unknown** the maintainer has not been asked.

Products added during the 2026-05-27 gap research (AgentGuard, AWS Secrets Manager Agent, Composio, DeepSecure, earl, faramesh-core, hasp, jentic-mini, mcp-governance-sdk, mcp-secrets-plugin, psst, sigcli, zeroid) are pending matrix verification with their maintainers and not yet rendered above.

## Products

Vaults, proxies, identity layers, and credential gateways. Alphabetical.

- [1Password CLI](products/1password-cli/) · `op run` substitutes `op://` secret references into a process environment at startup. Closed source, Go binary.
- [AgentGuard](products/agentguard/) · Runtime guardrail layer for agents: data loss path blocking, secret scrubbing, skill trust registry.
- [Authsome](products/authsome/) · Local OAuth2 and API-key vault. The agent never sees raw credentials. MIT, Python.
- [AWS Secrets Manager](products/aws-secrets-manager/) · IAM-scoped managed secret store with rotation. Proprietary.
- [AWS Secrets Manager Agent](products/aws-secretsmanager-agent/) · Official AWS sidecar exposing Secrets Manager over loopback. Apache 2.0, Rust.
- [Bitwarden Agent Access](products/bitwarden-agent-access/) · Open protocol for per-request human approval against a Bitwarden vault. Apache 2.0, Rust.
- [Botiverse agent-vault](products/botiverse-agent-vault/) · Local proxy that keeps secrets out of chat-agent context. Apache 2.0, TypeScript.
- [Composio](products/composio/) · Toolkit platform with 1000+ integrations and managed OAuth for agent frameworks. Apache 2.0.
- [DeepSecure](products/deepsecure/) · Identity, credential, and access management for AI agents and MCP servers.
- [Doppler](products/doppler/) · CLI that injects a project's secrets into a wrapped process. Apache 2.0, Go.
- [earl](products/earl/) · Rust CLI proxy with HCL operation templates, OS keychain secrets, MCP integration.
- [faramesh-core](products/faramesh-core/) · Governance-as-Code library for agent credential brokering.
- [hasp](products/hasp/) · Local-first broker for managed secrets in agent workflows. Go.
- [HashiCorp Vault](products/hashicorp-vault/) · General secrets platform with Vault Agent sidecars and an AI-agent-identity validated pattern. BUSL 1.1, Go.
- [Infisical Agent Vault](products/infisical-agent-vault/) · HTTPS proxy that swaps placeholder tokens for real credentials at the network layer. Source-available, Go.
- [jentic-mini](products/jentic-mini/) · Self-hosted API execution layer that injects credentials between agent and external APIs.
- [Keeper Agent Kit](products/keeper-agent-kit/) · Skill bundle wrapping Keeper Secrets Manager for coding agents. Apache 2.0, Shell.
- [Kontext CLI](products/kontext-cli/) · Wraps coding agents with RFC 8693 token-exchanged short-lived credentials. MIT, Go.
- [LiteLLM Agent Platform](products/litellm-agent-platform/) · Self-hosted platform running coding agents in isolated sandboxes with a vault proxy. MIT, TypeScript.
- [mcp-governance-sdk](products/mcp-governance-sdk/) · Enterprise governance layer (identity, RBAC, credentials, audit) for the MCP SDK.
- [mcp-secrets-plugin](products/mcp-secrets-plugin/) · OS-keychain credential management for MCP servers.
- [onecli](products/onecli/) · Single-binary credential gateway with a built-in vault for AI agents. Apache 2.0, TypeScript.
- [psst](products/psst/) · AI-native secrets manager using the OS keychain and a token-substitution model.
- [Pulumi ESC](products/pulumi-esc/) · Environments, secrets, and configuration service that composes secrets from many backends. Apache 2.0, Go.
- [sigcli](products/sigcli/) · Auth CLI and proxy for AI agents: "give agents access, not your credentials."
- [SOPS](products/sops/) · Encrypts files in place with KMS, age, or PGP. MPL 2.0, Go.
- [Wirken](products/wirken/) · Single-binary switchboard with encrypted vault, per-channel isolation, and hash-chained audit log. MIT, Rust.
- [zeroid](products/zeroid/) · Autonomous Agent Identity Management System using RFC 8693 token exchange and SPIFFE.

## Integrations

How each agent platform consumes credentials today. Alphabetical.

- [Aider](integrations/aider/) · `.env` and `.aider.conf.yml`. Ad hoc, env vars only.
- [AutoGen](integrations/autogen/) · Model client config plus tool env vars; conductor pattern inherits credentials across spawned agents.
- [Claude Code](integrations/claude-code/) · `settings.json` env, MCP `env` per server, pre/post-tool-use hooks, skills.
- [Cline](integrations/cline/) · VS Code extension settings, MCP config, inherited env. No first-party broker.
- [Codex CLI](integrations/codex/) · `~/.codex/config.toml`, per-provider `env_key`, optional OS keyring.
- [Continue.dev](integrations/continue-dev/) · `config.yaml` with `${{ secrets.NAME }}` resolved from `.env`, workspace `.env`, or Mission Control hub.
- [CrewAI](integrations/crewai/) · Tool constructors accept credentials at init time. Common pairing with Composio.
- [Cursor](integrations/cursor/) · `~/.cursor/mcp.json` with `${env:VAR}` interpolation. Remote-header interpolation broken.
- [Goose](integrations/goose/) · `~/.config/goose/config.yaml` plus per-extension env vars.
- [LangChain](integrations/langchain/) · `secret_from_env` returns `SecretStr` for log scrubbing.
- [LangGraph](integrations/langgraph/) · `RunnableConfig["configurable"]` plus the `Auth` handler for per-request secret resolution.
- [Mastra](integrations/mastra/) · `mastra server env import` (mode 0600); pluggable auth providers.
- [OpenAI Agents SDK](integrations/openai-agents-sdk/) · Lazy-read `OPENAI_API_KEY`, `set_default_openai_key`. Third-party tool creds are ad hoc.
- [OpenHands](integrations/openhands/) · Sandboxed container runtime; egress proxy is a natural injection point.
- [Pydantic AI](integrations/pydantic-ai/) · Provider env vars; Pydantic `SecretStr` scrubs logs.
- [Vercel AI SDK](integrations/vercel-ai-sdk/) · `process.env` inside `tool({ execute })`, Sensitive env vars, AI Gateway OIDC.
- [Windsurf](integrations/windsurf/) · `mcp_config.json` with `${env:VAR}` interpolation across `command`/`args`/`env`/`headers`/`url`.

## Services

Per-third-party-API credential recipes. Alphabetical.

- [Anthropic](services/anthropic/) · Workspace-scoped keys, admin keys held separately.
- [Cal.com](services/cal-com/) · OAuth client + managed-user access tokens (60m) and refresh (1y).
- [Cloudflare](services/cloudflare/) · API tokens with permission group, resource, IP, and TTL filters.
- [GitHub](services/github/) · GitHub App installation tokens (1h, repo-scoped).
- [HubSpot](services/hubspot/) · Private apps with minimum CRM scopes.
- [Linear](services/linear/) · OAuth with actor authorization for revocable, attributed writes.
- [Mailgun](services/mailgun/) · Domain sending keys bound to one verified domain.
- [Notion](services/notion/) · Public OAuth integration with rotating refresh tokens.
- [OpenAI](services/openai/) · Project-scoped service account keys with Restricted permissions.
- [Pinecone](services/pinecone/) · Project-scoped API keys (granular roles require Standard+).
- [Plaid](services/plaid/) · Per-user Item access tokens; rotate via `/item/access_token/invalidate`.
- [Resend](services/resend/) · Sending-access key bound to one verified domain.
- [Salesforce](services/salesforce/) · JWT Bearer flow with per-agent certificate and minimum scopes.
- [SendGrid](services/sendgrid/) · Custom (Restricted) access key with only `mail.send`.
- [Shopify](services/shopify/) · Custom-app Admin API token, read-only where possible.
- [Slack](services/slack/) · Bot tokens with granular scopes and 12h rotation.
- [Stripe](services/stripe/) · Restricted API keys (RAKs) with per-resource Read/Write.
- [Supabase](services/supabase/) · Secret key on the server, never the `service_role` JWT in agent reach.
- [Twilio](services/twilio/) · Per-agent Subaccount + Restricted API key.
- [Vercel](services/vercel/) · Team-scoped PATs with explicit expiry.

## Patterns

Named recipes. Each cites the project that best implements it.

- [Agents Rule of Two](patterns/agents-rule-of-two.md) · Hold at most two of {untrusted input, sensitive data, state change}.
- [Audit trails and SIEM integration](patterns/audit-trails-siem.md) · Per-agent identity, credential reference IDs (never values), pipe to SIEM.
- [Confused deputy across subagents](patterns/confused-deputy.md) · Authenticate the requesting agent, do not implicitly trust the caller.
- [Hook-based injection](patterns/hook-based-injection.md) · Resolve placeholders at the tool boundary, not in prompt context.
- [Just-in-time credential injection](patterns/just-in-time-injection.md) · Credentials supplied at the moment of the call, valid for minutes.
- [Lethal trifecta](patterns/lethal-trifecta.md) · Break at least one leg of {private data, untrusted input, outbound channel}.
- [Non-Human Identity (RFC 8693, SPIFFE)](patterns/non-human-identity.md) · Treat the agent as a principal, not a key holder.
- [Per-task credential scoping](patterns/per-task-scoping.md) · One narrow credential per task; revoke on completion.
- [Sandboxed egress for the agent process](patterns/sandboxed-egress.md) · Domain allowlist, JWT-authenticated proxy, network-level firewall.
- [Scoped delegation tokens](patterns/scoped-delegation-tokens.md) · Narrowest principal that works: GitHub App tokens, Stripe RAKs.
- [Secret redaction in prompts and logs](patterns/secret-redaction.md) · Placeholders in prompts, sanitisers on stdout.
- [Short-lived tokens with rotation](patterns/short-lived-tokens.md) · ~1h access tokens with rotated refresh tokens.
- [Subagent credential non-inheritance](patterns/subagent-non-inheritance.md) · Spawned subagents start with the least privilege their role requires.
- [Token substitution proxy](patterns/token-substitution-proxy.md) · Agent operates on opaque placeholders end to end; substitution is symmetric.

## Threat models

- [Browser-agent takeover](threat-models/browser-agent-takeover.md) · Agentic browser inheriting user sessions, password manager auto-unlock.
- [Indirect injection through shared data](threat-models/indirect-injection-data-exfil.md) · Untrusted instructions in shared documents, tickets, spreadsheets.
- [Logging-pipeline secret leakage](threat-models/logging-pipeline-leakage.md) · Credentials echoed to stdout, structured logs, observability backends.
- [Long-running agent rotation gaps](threat-models/long-running-rotation-gaps.md) · Multi-day agents outliving their tokens, 401s mid-task.
- [Over-scoped write credential](threat-models/over-scoped-write-credential.md) · One credential carrying delete on both production and backups.
- [Prompt-injection credential disclosure](threat-models/prompt-injection-exfiltration.md) · Untrusted text directing the agent to surface secrets via tool calls.
- [Shared-session leakage](threat-models/shared-session-leakage.md) · Multi-tenant agents bleeding secrets across users.
- [Skill and tool supply-chain](threat-models/skill-supply-chain.md) · Third-party skills inheriting the agent's credential surface.
- [Subagent credential inheritance](threat-models/subagent-inheritance.md) · Spawned subagents inheriting more privilege than their role needs.
- [Tool-use credential confusion](threat-models/tool-use-credential-confusion.md) · Agent invoking a tool with the wrong principal's credentials.

## Contributing

PRs welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) and [CATEGORY-MAP.md](CATEGORY-MAP.md) first. Every entry follows the same frontmatter and word-count shape. Direct competitors of the maintainer get accepted on equal terms.

## License

[CC0 1.0 Universal](LICENSE). Public domain dedication.

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs. Authsome is one of the products listed above. See [CATEGORY-MAP.md](CATEGORY-MAP.md) for how that is handled.
