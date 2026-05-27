---
name: Lethal trifecta
slug: lethal-trifecta
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: simon-willison
related: [agents-rule-of-two, sandboxed-egress]
---

# Lethal trifecta

An agent session becomes unsafe the moment it combines three capabilities in one place: access to private data, ingestion of untrusted content, and an outbound channel that can carry data out. Simon Willison coined the framing. Once all three co-exist, a single untrusted instruction in a document, email, or support ticket can chain through tool calls to send secrets somewhere the user did not intend.

## Defensive posture

Break at least one leg of the trifecta in any session that holds secrets. Common splits:

- Private data + outbound channel, untrusted content stays out of context.
- Private data + untrusted content, no outbound channel (read-only session).
- Untrusted content + outbound channel, no private data accessible (sandbox session).

## Reference implementation

Claude Code separates the three legs by default in restricted modes: the sandbox can disable outbound network access entirely, and `permissions.deny` keeps `.env` files out of the session that ingests untrusted text.

## Citation

- [Simon Willison: The Lethal Trifecta](https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
