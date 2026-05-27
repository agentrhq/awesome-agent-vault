---
name: AWS Secrets Manager Agent
slug: aws-secretsmanager-agent
type: product
license: Apache-2.0
stars: 656
last_verified: 2026-05-27
maintainer: aws
related: [aws-secrets-manager, hook-based-injection]
---

# AWS Secrets Manager Agent

Official AWS sidecar that exposes Secrets Manager as a local HTTP service. Built in Rust. Agents call `http://localhost:2773/secretsmanager/get?secretId=...` instead of using the SDK directly, which is the agent-side integration story for AWS Secrets Manager.

## Architecture

Runs locally next to the agent process. Caches secret values to avoid the per-request fetch cost of direct API calls. Authentication is the workload's IAM role; the sidecar handles the SDK call and returns the secret over loopback.

## Who it is for

AWS workloads running agents inside Lambda, ECS, EKS, or EC2 that want a cleaner local interface than the AWS SDK. Also fits non-AWS environments where the sidecar runs alongside the agent and authenticates via static IAM credentials (less ideal).

## Trade-offs

The sidecar still hands the agent process plaintext secrets over loopback; it is not a per-tool-call broker.

## Example

```bash
curl "http://localhost:2773/secretsmanager/get?secretId=agent/stripe" \
  -H "X-Aws-Parameters-Secrets-Token: $AGENT_TOKEN"
```

## Links

- Repo: [github.com/aws/aws-secretsmanager-agent](https://github.com/aws/aws-secretsmanager-agent)
- Last updated: 2026-05-19
- Stars: 656
- License: Apache-2.0
- Language: Rust

---

Curated by [Authsome](https://authsome.ai) · agent identity for third-party APIs.
