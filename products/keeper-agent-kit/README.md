---
name: Keeper Agent Kit
slug: keeper-agent-kit
type: product
license: Apache-2.0
stars: 7
last_verified: 2026-05-27
maintainer: Keeper-Security
related: [hook-based-injection]
---

# Keeper Agent Kit

Bundle of skills wrapping Keeper Secrets Manager and Commander so Claude Code, Cursor, Codex, and Copilot can pull Keeper secrets without putting them in chat. Released April 2026.

## Architecture

A set of Claude-skill-style packages plus CLI wrappers. The agent invokes a skill which fetches the requested secret from Keeper, applies it to the operation, and never returns the raw value to the chat surface.

## Who it is for

Keeper Security customers extending their existing vault to coding agents.

## Trade-offs

Tightly Keeper-locked. Skill bundle is still small (v1.1.0 as of May 2026). Non-Keeper backends are not supported.

## Example

```bash
git clone github.com/Keeper-Security/keeper-agent-kit
./install.sh
```

## Links

- Repo: [github.com/Keeper-Security/keeper-agent-kit](https://github.com/Keeper-Security/keeper-agent-kit)
- Latest release: v1.1.0 (2026-05-13)
- License: Apache-2.0
- Language: Shell

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
