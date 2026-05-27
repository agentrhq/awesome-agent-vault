---
name: Bitwarden Agent Access
slug: bitwarden-agent-access
type: product
license: Apache-2.0
stars: 73
last_verified: 2026-05-27
maintainer: bitwarden
related: [scoped-delegation-tokens, per-task-scoping]
---

# Bitwarden Agent Access

Open protocol plus CLI and SDK that lets an agent pull individual credentials from a Bitwarden vault with per-request human approval. The protocol is documented separately from the implementation so other vaults can adopt it.

## Architecture

The agent requests a specific credential by name; the Bitwarden client prompts the human user to approve the release; the credential is returned for the duration of one operation. There is no long-lived broker token in the agent process.

## Who it is for

Bitwarden-using developers who want vault-backed access for agents without exposing the entire vault. The approval-in-the-loop posture suits sensitive operations more than chat-driven flows.

## Trade-offs

Approval-in-the-loop is safe but creates friction for long-running autonomous sessions. Not a fit for fully unattended agents.

## Example

```bash
bw agent-access serve
# In the agent process
bw-agent get stripe-prod-key
```

## Links

- Repo: [github.com/bitwarden/agent-access](https://github.com/bitwarden/agent-access)
- Latest release: v0.11.0 (2026-03-21)
- License: Apache-2.0
- Language: Rust

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
