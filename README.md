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

Rows are products. Columns are agent platforms.

| Product | Claude Code | Codex CLI | Cursor | Aider | Windsurf | LangChain | OpenAI Agents SDK | Mastra | Vercel AI SDK | Continue.dev |
|---|---|---|---|---|---|---|---|---|---|---|
| [1Password CLI](products/1password-cli/) | ✅ | ✅ [^op-codex] | 🟡 | ✅ | 🟡 | ✅ | ✅ | ✅ | ✅ | ✅ |
| [Authsome](products/authsome/) | ✅ | ✅ | ✅ | ✅ | ✅ | 🟡 | 🟡 | 🟡 | 🟡 | ✅ |
| [AWS Secrets Manager](products/aws-secrets-manager/) | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | ✅ | ✅ | ✅ | ✅ | 🟡 |
| [Bitwarden Agent Access](products/bitwarden-agent-access/) | ✅ | 🟡 | 🟡 | - | - | 🟡 | 🟡 | - | - | - |
| [Botiverse agent-vault](products/botiverse-agent-vault/) | 🟡 | - | - | - | - | 🟡 | - | - | - | - |
| [Doppler](products/doppler/) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| [HashiCorp Vault](products/hashicorp-vault/) | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | ✅ | ✅ | ✅ | ✅ | 🟡 |
| [Infisical Agent Vault](products/infisical-agent-vault/) | ✅ | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 |
| [Keeper Agent Kit](products/keeper-agent-kit/) | ✅ | ✅ | ✅ | - | - | - | - | - | - | - |
| [Kontext CLI](products/kontext-cli/) | ✅ | ✅ | ✅ | 🟡 | 🟡 | - | - | - | - | 🟡 |
| [LiteLLM Agent Platform](products/litellm-agent-platform/) | ✅ | ✅ | 🟡 | 🟡 | 🟡 | ✅ | ✅ | 🟡 | 🟡 | 🟡 |
| [onecli](products/onecli/) | ✅ | ✅ | ✅ | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 |
| [Pulumi ESC](products/pulumi-esc/) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| [SOPS](products/sops/) | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 | 🟡 |
| [Wirken](products/wirken/) | 🟡 | 🟡 | - | - | - | - | - | - | - | - |

[^op-codex]: 1Password Environments MCP server shipped a Codex-first integration in May 2026.

Cell meanings: ✅ maintained adapter or first-party docs. 🟡 can be wired in, requires custom glue. `-` no public path. `?` maintainer has not been asked.

Products added during the 2026-05-27 gap research (AgentGuard, AWS Secrets Manager Agent, Composio, DeepSecure, earl, faramesh-core, hasp, jentic-mini, mcp-governance-sdk, mcp-secrets-plugin, psst, sigcli, zeroid) are pending matrix verification with their maintainers and not yet rendered above.

## Products

Vaults, proxies, identity layers, and credential gateways. Alphabetical. Entry name links to the upstream project; `(details)` opens our notes.

- [1Password CLI](https://developer.1password.com/docs/cli/) · `op run` substitutes `op://` secret references into a process environment at startup. Closed source, Go binary. ([details](products/1password-cli/))
- [AgentGuard](https://github.com/GoPlusSecurity/agentguard) · Runtime guardrail layer for agents: data loss path blocking, secret scrubbing, skill trust registry. ([details](products/agentguard/))
- [Authsome](https://github.com/agentrhq/authsome) · Local OAuth2 and API-key vault. The agent never sees raw credentials. MIT, Python. ([details](products/authsome/))
- [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/) · IAM-scoped managed secret store with rotation. Proprietary. ([details](products/aws-secrets-manager/))
- [AWS Secrets Manager Agent](https://github.com/aws/aws-secretsmanager-agent) · Official AWS sidecar exposing Secrets Manager over loopback. Apache 2.0, Rust. ([details](products/aws-secretsmanager-agent/))
- [Bitwarden Agent Access](https://github.com/bitwarden/agent-access) · Open protocol for per-request human approval against a Bitwarden vault. Apache 2.0, Rust. ([details](products/bitwarden-agent-access/))
- [Botiverse agent-vault](https://github.com/botiverse/agent-vault) · Local proxy that keeps secrets out of chat-agent context. Apache 2.0, TypeScript. ([details](products/botiverse-agent-vault/))
- [Composio](https://github.com/ComposioHQ/composio) · Toolkit platform with 1000+ integrations and managed OAuth for agent frameworks. Apache 2.0. ([details](products/composio/))
- [DeepSecure](https://github.com/DeepTrail/deepsecure) · Identity, credential, and access management for AI agents and MCP servers. ([details](products/deepsecure/))
- [Doppler](https://github.com/DopplerHQ/cli) · CLI that injects a project's secrets into a wrapped process. Apache 2.0, Go. ([details](products/doppler/))
- [earl](https://github.com/mathematic-inc/earl) · Rust CLI proxy with HCL operation templates, OS keychain secrets, MCP integration. ([details](products/earl/))
- [faramesh-core](https://github.com/faramesh/faramesh-core) · Governance-as-Code library for agent credential brokering. ([details](products/faramesh-core/))
- [hasp](https://github.com/gethasp/hasp) · Local-first broker for managed secrets in agent workflows. Go. ([details](products/hasp/))
- [HashiCorp Vault](https://github.com/hashicorp/vault) · General secrets platform with Vault Agent sidecars and an AI-agent-identity validated pattern. BUSL 1.1, Go. ([details](products/hashicorp-vault/))
- [Infisical Agent Vault](https://github.com/Infisical/agent-vault) · HTTPS proxy that swaps placeholder tokens for real credentials at the network layer. Source-available, Go. ([details](products/infisical-agent-vault/))
- [jentic-mini](https://github.com/jentic/jentic-mini) · Self-hosted API execution layer that injects credentials between agent and external APIs. ([details](products/jentic-mini/))
- [Keeper Agent Kit](https://github.com/Keeper-Security/keeper-agent-kit) · Skill bundle wrapping Keeper Secrets Manager for coding agents. Apache 2.0, Shell. ([details](products/keeper-agent-kit/))
- [Kontext CLI](https://github.com/kontext-security/kontext-cli) · Wraps coding agents with RFC 8693 token-exchanged short-lived credentials. MIT, Go. ([details](products/kontext-cli/))
- [LiteLLM Agent Platform](https://github.com/BerriAI/litellm-agent-platform) · Self-hosted platform running coding agents in isolated sandboxes with a vault proxy. MIT, TypeScript. ([details](products/litellm-agent-platform/))
- [mcp-governance-sdk](https://github.com/ithena-one/mcp-governance-sdk) · Enterprise governance layer (identity, RBAC, credentials, audit) for the MCP SDK. ([details](products/mcp-governance-sdk/))
- [mcp-secrets-plugin](https://github.com/amirshk/mcp-secrets-plugin) · OS-keychain credential management for MCP servers. ([details](products/mcp-secrets-plugin/))
- [onecli](https://github.com/onecli/onecli) · Single-binary credential gateway with a built-in vault for AI agents. Apache 2.0, TypeScript. ([details](products/onecli/))
- [psst](https://github.com/Michaelliv/psst) · AI-native secrets manager using the OS keychain and a token-substitution model. ([details](products/psst/))
- [Pulumi ESC](https://github.com/pulumi/esc) · Environments, secrets, and configuration service that composes secrets from many backends. Apache 2.0, Go. ([details](products/pulumi-esc/))
- [sigcli](https://github.com/sigcli/sigcli) · Auth CLI and proxy for AI agents: "give agents access, not your credentials." ([details](products/sigcli/))
- [SOPS](https://github.com/getsops/sops) · Encrypts files in place with KMS, age, or PGP. MPL 2.0, Go. ([details](products/sops/))
- [Wirken](https://github.com/gebruder/wirken) · Single-binary switchboard with encrypted vault, per-channel isolation, and hash-chained audit log. MIT, Rust. ([details](products/wirken/))
- [zeroid](https://github.com/highflame-ai/zeroid) · Autonomous Agent Identity Management System using RFC 8693 token exchange and SPIFFE. ([details](products/zeroid/))

## Integrations

How each agent platform consumes credentials today. Alphabetical. Entry name links to the upstream project; `(details)` opens our notes.

- [Aider](https://aider.chat) · `.env` and `.aider.conf.yml`. Ad hoc, env vars only. ([details](integrations/aider/))
- [AutoGen](https://github.com/microsoft/autogen) · Model client config plus tool env vars; conductor pattern inherits credentials across spawned agents. ([details](integrations/autogen/))
- [Claude Code](https://code.claude.com/docs/en/settings) · `settings.json` env, MCP `env` per server, pre/post-tool-use hooks, skills. ([details](integrations/claude-code/))
- [Cline](https://github.com/cline/cline) · VS Code extension settings, MCP config, inherited env. No first-party broker. ([details](integrations/cline/))
- [Codex CLI](https://developers.openai.com/codex/config-reference) · `~/.codex/config.toml`, per-provider `env_key`, optional OS keyring. ([details](integrations/codex/))
- [Continue.dev](https://docs.continue.dev/reference) · `config.yaml` with `${{ secrets.NAME }}` resolved from `.env`, workspace `.env`, or Mission Control hub. ([details](integrations/continue-dev/))
- [CrewAI](https://github.com/crewAIInc/crewAI) · Tool constructors accept credentials at init time. Common pairing with Composio. ([details](integrations/crewai/))
- [Cursor](https://docs.cursor.com/context/model-context-protocol) · `~/.cursor/mcp.json` with `${env:VAR}` interpolation. Remote-header interpolation broken. ([details](integrations/cursor/))
- [Goose](https://github.com/block/goose) · `~/.config/goose/config.yaml` plus per-extension env vars. ([details](integrations/goose/))
- [LangChain](https://python.langchain.com/api_reference/core/utils/langchain_core.utils.utils.secret_from_env.html) · `secret_from_env` returns `SecretStr` for log scrubbing. ([details](integrations/langchain/))
- [LangGraph](https://docs.langchain.com/langgraph-platform/custom-auth) · `RunnableConfig["configurable"]` plus the `Auth` handler for per-request secret resolution. ([details](integrations/langgraph/))
- [Mastra](https://mastra.ai/reference/configuration) · `mastra server env import` (mode 0600); pluggable auth providers. ([details](integrations/mastra/))
- [OpenAI Agents SDK](https://openai.github.io/openai-agents-python/config/) · Lazy-read `OPENAI_API_KEY`, `set_default_openai_key`. Third-party tool creds are ad hoc. ([details](integrations/openai-agents-sdk/))
- [OpenHands](https://github.com/All-Hands-AI/OpenHands) · Sandboxed container runtime; egress proxy is a natural injection point. ([details](integrations/openhands/))
- [Pydantic AI](https://ai.pydantic.dev) · Provider env vars; Pydantic `SecretStr` scrubs logs. ([details](integrations/pydantic-ai/))
- [Vercel AI SDK](https://vercel.com/docs/ai-gateway/authentication-and-byok) · `process.env` inside `tool({ execute })`, Sensitive env vars, AI Gateway OIDC. ([details](integrations/vercel-ai-sdk/))
- [Windsurf](https://docs.windsurf.com/windsurf/cascade/mcp) · `mcp_config.json` with `${env:VAR}` interpolation across `command`/`args`/`env`/`headers`/`url`. ([details](integrations/windsurf/))

## Services

Per-third-party-API credential recipes. Alphabetical. Entry name links to the canonical credential docs; `(recipe)` opens our agent-specific notes.

- [Anthropic](https://platform.claude.com/docs/en/build-with-claude/workspaces) · Workspace-scoped keys, admin keys held separately. ([recipe](services/anthropic/))
- [Cal.com](https://cal.com/docs/api-reference/v2/introduction) · OAuth client + managed-user access tokens (60m) and refresh (1y). ([recipe](services/cal-com/))
- [Cloudflare](https://developers.cloudflare.com/fundamentals/api/get-started/create-token/) · API tokens with permission group, resource, IP, and TTL filters. ([recipe](services/cloudflare/))
- [GitHub](https://docs.github.com/en/apps/creating-github-apps/authenticating-with-a-github-app/authenticating-as-a-github-app-installation) · GitHub App installation tokens (1h, repo-scoped). ([recipe](services/github/))
- [HubSpot](https://developers.hubspot.com/docs/guides/apps/private-apps/overview) · Private apps with minimum CRM scopes. ([recipe](services/hubspot/))
- [Linear](https://linear.app/developers) · OAuth with actor authorization for revocable, attributed writes. ([recipe](services/linear/))
- [Mailgun](https://documentation.mailgun.com/docs/mailgun/api-reference/send/mailgun/domain-keys) · Domain sending keys bound to one verified domain. ([recipe](services/mailgun/))
- [Notion](https://developers.notion.com/docs/authorization) · Public OAuth integration with rotating refresh tokens. ([recipe](services/notion/))
- [OpenAI](https://platform.openai.com/docs/guides/rbac) · Project-scoped service account keys with Restricted permissions. ([recipe](services/openai/))
- [Pinecone](https://docs.pinecone.io/guides/projects/manage-api-keys) · Project-scoped API keys (granular roles require Standard+). ([recipe](services/pinecone/))
- [Plaid](https://plaid.com/docs/api/items/) · Per-user Item access tokens; rotate via `/item/access_token/invalidate`. ([recipe](services/plaid/))
- [Resend](https://resend.com/docs/dashboard/api-keys/introduction) · Sending-access key bound to one verified domain. ([recipe](services/resend/))
- [Salesforce](https://help.salesforce.com/s/articleView?id=sf.remoteaccess_oauth_jwt_flow.htm) · JWT Bearer flow with per-agent certificate and minimum scopes. ([recipe](services/salesforce/))
- [SendGrid](https://www.twilio.com/docs/sendgrid/ui/account-and-settings/api-keys) · Custom (Restricted) access key with only `mail.send`. ([recipe](services/sendgrid/))
- [Shopify](https://shopify.dev/docs/apps/build/authentication-authorization/access-tokens/generate-app-access-tokens-admin) · Custom-app Admin API token, read-only where possible. ([recipe](services/shopify/))
- [Slack](https://docs.slack.dev/authentication/tokens) · Bot tokens with granular scopes and 12h rotation. ([recipe](services/slack/))
- [Stripe](https://docs.stripe.com/keys/restricted-api-keys) · Restricted API keys (RAKs) with per-resource Read/Write. ([recipe](services/stripe/))
- [Supabase](https://supabase.com/docs/guides/api/api-keys) · Secret key on the server, never the `service_role` JWT in agent reach. ([recipe](services/supabase/))
- [Twilio](https://www.twilio.com/docs/iam/api-keys) · Per-agent Subaccount + Restricted API key. ([recipe](services/twilio/))
- [Vercel](https://vercel.com/docs/sign-in-with-vercel/scopes-and-permissions) · Team-scoped PATs with explicit expiry. ([recipe](services/vercel/))

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

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs. Authsome is one of the products listed above. See [CATEGORY-MAP.md](CATEGORY-MAP.md) for how that is handled.
