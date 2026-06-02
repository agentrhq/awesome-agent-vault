---
name: Process enumeration disclosure
slug: process-enumeration-disclosure
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: n/a
related: ["secret-redaction","hook-based-injection"]
---

# Process enumeration disclosure

Secrets passed through environment variables are readable by any process running as the same user, and sometimes by other users depending on kernel policy. Once a credential lands in `environ`, it persists for the lifetime of the process and is copied into every child the agent spawns unless the parent explicitly scrubs it.

## Surface

- `/proc/<pid>/environ` on Linux, readable by the owning UID and by root.
- `ps eww`, `ps auxe`, and equivalent procfs walkers on systems where `hidepid` is not enforced.
- macOS `ps -E` and `libproc` calls from same-user processes.
- Subprocesses spawned via `os.execvpe`, `subprocess.Popen`, `child_process.spawn`, or shell `exec` that inherit the parent environment by default.
- Crash dumps, core files, and `/proc/<pid>/status` style metadata captured by telemetry agents.
- Container runtimes that expose the host `/proc` into sidecars or debug pods.

## Mitigations

- Avoid putting raw secrets in environment variables at all. Inject per-request via a local broker. See [../patterns/local-broker-proxy.md](../patterns/local-broker-proxy.md).
- Scrub the environment before exec. See [../patterns/hook-based-injection.md](../patterns/hook-based-injection.md).
- Mount `/proc` with `hidepid=2` on Linux hosts that run agents.
- Use short-lived tokens so a leaked `environ` snapshot expires quickly.
- Redact secrets from logs and crash reports. See [../patterns/secret-redaction.md](../patterns/secret-redaction.md).

## Citation

- [Authsome threat model: process enumeration](https://authsome.ai/docs/security/threat-model.md)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
