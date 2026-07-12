# delivery-copilot

> Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.

**Domain:** devops | **Complexity:** expert | **Stack:** Go, Argo Rollouts, Crossplane, Terraform, Vault, OTel, Prometheus, Multi-cluster

| | |
|---|---|
| Use case | Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails. |
| Pain point | Teams still fight slow manual work, unclear ownership, and brittle handoffs when delivery is under pressure. |
| Success metric | Cut review time by 70% and reduce recovery effort for delivery by half. |
| Cost | $0/mo on Cloudflare |

## Why this exists

Teams still fight slow manual work, unclear ownership, and brittle handoffs when delivery is under pressure.. Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.

> This project automates deploy pipelines, drift detection, and rollback safety for modern engineering teams. For this implementation, the service is designed to remove the operational friction behind Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails..

## What this product does

This project ships a production-oriented service that exposes health, readiness, observability, and domain-specific endpoints for Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.. The implementation is intended to be deployed behind Kubernetes with secure defaults, CI validation, and rollback-ready manifests.

## Quick start

```bash
docker build -t delivery-copilot:local .
docker run -p 8080:8080 delivery-copilot:local
curl http://localhost:8080/healthz
```

## Architecture

```
GitHub CI -> Container Registry -> Kubernetes -> Go -> Operators / SRE
```

See `docs/ARCHITECTURE.md`

## Infrastructure

Full spec: `terraform/INFRA_REQUIREMENTS.md`

TL;DR: K8s cluster, 2-10 pods HPA, $0 on Cloudflare

## Docs

- `docs/ARCHITECTURE.md` - components, tradeoffs
- `docs/DESIGN_DISCUSSION.md` - how we decided to build this
- `docs/DEPLOYMENT.md` - GitOps, rollback
- `docs/SECURITY.md` - threat model
- `docs/TROUBLESHOOTING.md` - 3am runbook
- `terraform/INFRA_REQUIREMENTS.md` - **infra: CPU/RAM/storage/cost**

Interview prep: `interview/`
