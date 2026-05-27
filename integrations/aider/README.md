---
name: Aider
slug: aider
type: integration
license: Apache-2.0
stars: n/a
last_verified: 2026-05-27
maintainer: paul-gauthier
related: []
---

# Aider

Aider has no hook system and no first-party secrets surface beyond `.env`. The YAML config refuses to hold anything but OpenAI and Anthropic keys, so other providers must use a `.env` file.

## Default mechanism

- `.env` file (preferred).
- `.aider.conf.yml` for OpenAI and Anthropic keys only.
- `--api-key provider=KEY` flag sets `PROVIDER_API_KEY` at startup.

## Injection surface

None. Env vars only.

## Notes

For non-trivial agent setups, wrap Aider in a credential proxy or `op run` to keep the secret out of the developer's shell history. Aider itself does not help.

## Docs

- [API keys](https://aider.chat/docs/config/api-keys.html)
- [.env](https://aider.chat/docs/config/dotenv.html)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
