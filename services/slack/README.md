---
name: Slack
slug: slack
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: slack
related: [scoped-delegation-tokens, short-lived-tokens]
---

# Slack

Slack has one of the most granular scope systems in the category. Bot tokens (`xoxb-`) carry only the scopes the app requests, workflow tokens (`xwfp-`) expire in 15 minutes, and token rotation refreshes bot tokens every 12 hours when enabled.

## Credential types

- **Bot token** (`xoxb-`): long-lived by default; supports rotation (12h refresh).
- **User token** (`xoxp-`): acts as a specific user. Avoid for agents.
- **Workflow token** (`xwfp-`): 15m, for function-step calls.
- **App-level token** (`xapp-`): for Socket Mode connections.
- **Configuration tokens**: for app management. Keep these out of agent reach entirely.

## Recommended pattern

Build a Slack app with only the granular scopes the task needs, enable token rotation, and let the agent refresh on its own. For ephemeral function steps, use workflow tokens.

## Critical scopes to refuse

`chat:write.public`, `files:write`, `channels:manage`, `users:write`, `admin.*`, `im:history`. Default to `chat:write` on a specific channel only.

## Rotation

Enable token rotation: bot tokens refresh every 12h. Rotate on workspace admin change.

## Example

```bash
curl -H "Authorization: Bearer xoxb-..." \
  -F "channel=C012345" -F "text=hello" \
  https://slack.com/api/chat.postMessage
```

## Docs

- [Slack token types](https://docs.slack.dev/authentication/tokens)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
