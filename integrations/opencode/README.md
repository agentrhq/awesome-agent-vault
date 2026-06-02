---
name: OpenCode
slug: opencode
type: integration
license: MIT
stars: n/a
last_verified: 2026-05-28
maintainer: anomalyco
related: [hook-based-injection]
---

# OpenCode

Open source terminal AI coding agent (npm: `opencode-ai`, site: opencode.ai). Originally `sst/opencode`, now under `anomalyco/opencode`. Active and widely adopted.

## Default mechanism

- Per-provider credentials stored via `opencode auth login <provider>`, persisted under the user's OpenCode config dir (typically `~/.local/share/opencode/` on Linux, `~/Library/Application Support/opencode/` on macOS).
- Provider env vars (`OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, `GROQ_API_KEY`, etc.) are read at startup if present.

## Injection surface

- MCP server config carries per-server credentials, same shape as Claude Code and Cursor.
- The auth subcommand stores tokens in a single JSON file; treat it as a sensitive file.

## Notes

For agent setups that need credentials brokered per call rather than per process, wrap OpenCode in a credential proxy (Authsome, Infisical Agent Vault, onecli). The auth file is convenient but is a single point of disclosure if the file is read by anything else with shell access.

## Docs

- Repo: [github.com/sst/opencode](https://github.com/sst/opencode)
- Site: [opencode.ai](https://opencode.ai)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
