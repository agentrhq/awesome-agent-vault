---
name: AWS Secrets Manager
slug: aws-secrets-manager
type: product
license: proprietary
stars: n/a
last_verified: 2026-05-27
maintainer: aws
related: [just-in-time-injection, short-lived-tokens]
---

# AWS Secrets Manager

Managed secret store with IAM-scoped retrieval, rotation, and SDK access. Agents running inside AWS (Lambda, ECS, EKS) can fetch secrets using the workload's IAM role rather than holding a long-lived static credential.

## Architecture

Each secret has a resource policy. Workloads call `secretsmanager:GetSecretValue` with their IAM identity; access is gated by the resource policy and the workload's IAM role. Rotation is a first-class feature for supported backing services.

## Who it is for

AWS-native teams whose agents already run inside Lambda, ECS, or EKS with IAM identities.

## Trade-offs

Cloud lock-in. Per-request fetch cost. No agent-specific just-in-time UX out of the box; agent identity is workload identity, which is IAM-shaped rather than agent-shaped.

## Example

```python
import boto3
secret = boto3.client("secretsmanager").get_secret_value(SecretId="agent/stripe")["SecretString"]
```

## Links

- Docs: [docs.aws.amazon.com/secretsmanager](https://docs.aws.amazon.com/secretsmanager/)
- License: proprietary

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
