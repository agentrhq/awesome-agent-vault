---
name: Offline disk-image theft
slug: offline-disk-image-theft
type: threat-model
license: n/a
stars: n/a
last_verified: 2026-05-28
maintainer: n/a
related: ["audit-trails-siem"]
---

# Offline disk-image theft

A vault file at rest is no safer than the disk it sits on. A stolen laptop, a misplaced external drive, or an unencrypted backup yields any unencrypted vault to whoever reads the bytes. Strong at-rest encryption, with the master key held outside the vault file itself, bounds the disclosure surface to data the attacker can actively decrypt rather than passively copy.

## Surface

- Stolen or lost laptops and workstations carrying a developer vault.
- Backup archives written to external drives, NAS, or cloud sync folders.
- Disk images and snapshots produced by IT for incident response or imaging.
- Decommissioned drives that bypass secure-wipe procedures.
- Shared developer machines where one user can read another's home directory.
- CI runners and ephemeral VMs that persist vault state to detachable volumes.

## Mitigations

- Envelope encryption with a master key resident in the OS keyring (macOS Keychain, Windows DPAPI, libsecret) so the vault file alone is insufficient to decrypt.
- Full-disk encryption (FileVault, BitLocker, LUKS) as a baseline layer beneath the vault.
- Per-record encryption so partial file recovery does not yield bulk plaintext.
- Short-lived credentials and rotation, so a stolen vault expires quickly.
- Backup hygiene: encrypt backups separately, exclude vault paths from sync folders by default.
- Remote wipe and device-attestation gates for any machine permitted to hold a vault.

## Citation

- [Authsome encryption docs](https://authsome.ai/docs/security/encryption.md)

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
