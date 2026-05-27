---
name: Wirken
slug: wirken
type: product
license: MIT
stars: 150
last_verified: 2026-05-27
maintainer: gebruder
related: [audit-trails-siem, sandboxed-egress]
---

# Wirken

Single-binary switchboard with an encrypted vault, per-channel isolation, and a hash-chained audit log. Designed for wiring agents into chat channels (Slack, Telegram, Matrix, Discord, WhatsApp) with a tamper-evident record.

## Architecture

Each chat channel gets an isolated credential namespace. The hash-chained audit log makes after-the-fact tampering detectable. Outbound API calls run through the switchboard, which applies the channel-scoped credential.

## Who it is for

Solo operators wiring agents into multiple chat channels who need an audit trail per channel.

## Trade-offs

Heavy bias toward chat-channel orchestration. A pure coding-agent setup gets less value from the per-channel isolation model.

## Example

```bash
wirken init --vault-key $WIRKEN_VAULT_KEY
wirken channel add slack --secret xoxb-...
wirken serve
```

## Links

- Repo: [github.com/gebruder/wirken](https://github.com/gebruder/wirken)
- Latest release: v2.0.1 (2026-05-19)
- License: MIT
- Language: Rust

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
