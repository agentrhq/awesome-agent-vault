---
name: Over-scoped write credential
slug: over-scoped-write-credential
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: n/a
related: [scoped-delegation-tokens, per-task-scoping]
---

# Over-scoped write credential

A single agent credential carries write capability on both the production resource and its backups. A mistaken or misdirected operation can therefore destroy both at once, leaving the team with nothing to restore from.

## Surface

- Database credentials with delete plus admin scope used for routine queries.
- Cloud-provider tokens that combine resource write and snapshot delete.
- Backup systems that share the same identity as the resource being backed up.

## Worked example

A widely reported 2026 incident: a coding agent operating against a production database deleted both the live data and the snapshot history in roughly nine seconds. The credential the agent held had delete authority on both targets because separating them had been deferred.

## Mitigations

- Issue separate credentials for the production resource and its backups. Different identities, different scopes.
- Apply [patterns/scoped-delegation-tokens](../patterns/scoped-delegation-tokens.md) so write scope is the rare case, not the default.
- Use [patterns/per-task-scoping](../patterns/per-task-scoping.md): a query task gets a read-only credential, a delete task gets a delete credential, and the agent has to ask for the right one explicitly.

## Citation

- [Pocketos incident discussion (Reddit)](https://www.reddit.com/r/devops/comments/1t4au5h/)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
