---
name: Kontext CLI
slug: kontext-cli
type: product
license: MIT
stars: 199
last_verified: 2026-05-27
maintainer: kontext-security
related: [short-lived-tokens, audit-trails-siem, scoped-delegation-tokens]
---

# Kontext CLI

Wraps coding agents with short-lived, RFC 8693 token-exchanged credentials and streams every tool call to an audit dashboard. The CLI is open source; the dashboard is a hosted SaaS.

## Architecture

The CLI exchanges a developer's identity for a narrowly scoped, short-lived token using RFC 8693 token exchange. Every tool call is signed and streamed to the audit pipeline. Approvals can be required for high-risk operations.

## Who it is for

Teams that want enterprise IAM (scoped tokens, audit, approvals) layered on top of CLI coding agents without rebuilding the broker themselves.

## Trade-offs

The SaaS dashboard is the real product; the CLI alone has limited value. Teams that need a fully self-hosted solution will look elsewhere.

## Example

```bash
kontext run --policy agent-readonly -- claude
```

## Links

- Repo: [github.com/kontext-security/kontext-cli](https://github.com/kontext-security/kontext-cli)
- Latest release: v0.8.1 (2026-05-20)
- License: MIT
- Language: Go

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
