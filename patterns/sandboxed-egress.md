---
name: Sandboxed egress for the agent process
slug: sandboxed-egress
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: anthropic
related: [lethal-trifecta, hook-based-injection]
---

# Sandboxed egress for the agent process

Even with strong credential discipline, a compromised agent process needs somewhere to send data out. Restrict outbound traffic at the network boundary using a domain allowlist, a JWT-authenticated proxy, and TLS inspection. Three independent layers, because any one of them can be bypassed in isolation.

## Mechanics

- Layer one: network firewall blocking direct outbound TCP.
- Layer two: domain-allowlisted egress proxy on top of Linux bubblewrap or macOS seatbelt.
- Layer three: JWT-authenticated proxy with TLS inspection for unexpected destinations.

Each layer fails independently. A single missing layer is still acceptable; a single layer doing everything is not.

## Reference implementation

Claude Code's sandbox uses bubblewrap on Linux and seatbelt on macOS with a domain-allowlisted egress proxy. The Claude Managed Agents tier adds a JWT-authenticated proxy and a network-level firewall. Two disclosed bypasses of the egress proxy (SOCKS5 null-byte handling) show why three independent layers matter; either alone was insufficient.

## Citations

- [Anthropic: Claude Code sandboxing](https://www.anthropic.com/engineering/claude-code-sandboxing)
- [Aonan Guan: second-time sandbox bypass write-up](https://oddguan.com/blog/second-time-same-sandbox-anthropic-claude-code-network-allowlist-bypass-data-exfiltration/)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
