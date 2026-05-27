---
name: Short-lived tokens with rotation
slug: short-lived-tokens
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [just-in-time-injection, long-running-rotation-gaps]
---

# Short-lived tokens with rotation

Static keys that live for years are incompatible with agents that ingest text from outside the trust boundary. OAuth access tokens that expire in roughly an hour with rotated refresh tokens shrink the window of damage if a token is observed, and force the system to prove identity continuously rather than once at provisioning.

## Mechanics

Refresh token rotation is the canonical pattern: each refresh response returns a new refresh token, and the old one is invalidated. A previously captured refresh token is single-use, so the time window where it has value is the gap between capture and the legitimate next refresh.

## Reference implementation

Auth0's published guidance is the most thorough public description. The same shape appears in Cal.com (60m access tokens), Slack (12h bot tokens with rotation enabled), and GitHub App installation tokens (1h).

## Citation

- [Auth0: Refresh token rotation](https://auth0.com/docs/secure/tokens/refresh-tokens/refresh-token-rotation)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
