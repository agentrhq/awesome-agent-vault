---
name: Headless OAuth via device-code flow
slug: device-code-headless-oauth
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: ietf
related: ["scoped-delegation-tokens","short-lived-tokens"]
---

# Headless OAuth via device-code flow

The device-code grant defined in RFC 8628 extends OAuth 2.0 to clients that cannot host a browser or receive a redirect callback. An agent running on a headless host requests a short user code from the authorization server, displays it alongside a verification URL, and waits. The human completes the browser leg on a separate device. The pattern removes the need to embed a client secret on the agent host or to expose a public redirect endpoint, which is the usual blocker for CI runners, SSH sessions, cron jobs, and containers.

## Mechanics

The agent calls the device authorization endpoint and receives a device code, a user code, a verification URI, and a polling interval. It surfaces the user code and URI to the operator through stdout, a chat message, or a desktop notification. The operator opens the URI on any browser-capable device, signs in, and approves the requested scopes. The agent polls the token endpoint with the device code. Until approval, the server returns `authorization_pending` or `slow_down`. Once the operator approves, the next poll returns an access token and refresh token bound to the granted scopes. Token rotation and revocation follow the same rules as any other OAuth grant.

## Reference implementation

GitHub's CLI uses the device-code flow for `gh auth login` on machines without a browser, and the same endpoint is reused by agent runtimes that wrap GitHub credentials. See [github-cli](/sites/github-cli/) for the entry in this index.

## Citation

- [RFC 8628: OAuth 2.0 Device Authorization Grant](https://datatracker.ietf.org/doc/html/rfc8628)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
