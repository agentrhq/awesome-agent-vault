---
name: Shell history exposure
slug: shell-history-exposure
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: n/a
related: ["secret-redaction","logging-pipeline-leakage"]
---

# Shell history exposure

Agents that drive a real shell tend to inline secrets directly on the command line. Those tokens are written to the user's history file before the process exits and persist across reboots. Anything that can read the home directory later (a different agent run, a backup, a leaked dotfile sync) can recover them.

## Surface

- `curl -u <key>:` and `curl -H "Authorization: Bearer <token>"` invocations.
- `export TOKEN=...` and `TOKEN=... command` prefix assignments.
- `psql`, `mysql`, `redis-cli` connection strings with embedded passwords.
- `git clone https://<user>:<pat>@github.com/...` URLs.
- `~/.bash_history`, `~/.zsh_history`, `~/.local/share/fish/fish_history`.
- Terminal multiplexer scrollback (tmux, screen) and IDE integrated terminals.
- Shell completion caches and recently-used command menus.

## Mitigations

- Inject credentials through a proxy or vault rather than as CLI arguments. See [../patterns/credential-injection-proxy.md](../patterns/credential-injection-proxy.md).
- Redact secret-shaped strings before any write to disk. See [../patterns/secret-redaction.md](../patterns/secret-redaction.md).
- Set `HISTFILE=/dev/null` or `HISTCONTROL=ignorespace` for agent shells and prefix sensitive commands with a leading space.
- Prefer config files with `0600` permissions over inline flags for tools that support both.
- Rotate any token that has ever appeared on a command line.

## Citation

- [Authsome threat model: shell history](https://authsome.ai/docs/security/threat-model.md)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
