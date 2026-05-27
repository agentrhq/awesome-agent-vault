---
name: Scoped delegation tokens
slug: scoped-delegation-tokens
type: pattern
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [short-lived-tokens, per-task-scoping]
---

# Scoped delegation tokens

Hand the agent the narrowest principal that works for the task, not the broadest one available. The two strongest references in this category are GitHub App installation tokens and Stripe Restricted API Keys.

## How it works

- **GitHub App installation tokens** are scoped per installation, expire in one hour, and can be further restricted to specific repositories within the installation.
- **Stripe Restricted API Keys** let you choose Read, Write, or None per resource type. Stripe's documentation recommends them "especially when giving a key to an AI agent."

The shared shape: a token that names what it can touch and an expiry that bounds the window. Both pieces are necessary; either alone is insufficient.

## Reference implementation

Stripe's RAK system in [services/stripe](../services/stripe/) is the cleanest documented example, with the GitHub App flow in [services/github](../services/github/) as the open-platform equivalent.

## Citations

- [GitHub: Authenticating as a GitHub App installation](https://docs.github.com/en/apps/creating-github-apps/authenticating-with-a-github-app/authenticating-as-a-github-app-installation)
- [Stripe: Restricted API keys](https://docs.stripe.com/keys/restricted-api-keys)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
