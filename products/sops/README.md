---
name: SOPS
slug: sops
type: product
license: MPL-2.0
stars: 21904
last_verified: 2026-05-27
maintainer: getsops
related: [hook-based-injection]
---

# SOPS

Encrypts files in place with KMS, age, or PGP. Secrets get decrypted to disk or piped to a process at runtime. Not designed for agents specifically, but useful when a team keeps secrets in git and needs an agent to read decrypted values at run time.

## Architecture

SOPS encrypts the values inside YAML, JSON, .env, or INI files, leaving the keys readable. Decryption uses one of the configured providers. `sops exec-env` decrypts and exports secrets into a wrapped process.

## Who it is for

Ops teams who keep secrets in git and want agents to read decrypted files at run time.

## Trade-offs

File-centric. No concept of agent identity, brokering, or per-tool-call audit. Suitable as a backend for a richer agent vault product; not a vault product itself.

## Example

```bash
sops exec-env agent-secrets.enc.yaml -- claude
```

## Links

- Repo: [github.com/getsops/sops](https://github.com/getsops/sops)
- Latest release: v1.7.3 (2026-05-26)
- License: MPL-2.0
- Language: Go

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
