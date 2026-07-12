# Architecture - delivery-copilot

> Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.

**Pain:** Teams still fight slow manual work, unclear ownership, and brittle handoffs when delivery is under pressure.  
**Success metric:** Cut review time by 70% and reduce recovery effort for delivery by half.

## Decision log

We chose K8s + go because the service needs to be deployed, observed, and rolled back under real production conditions. The architecture reflects the operational problem behind Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.: we need something that ships quickly, is observable, and can be recovered without hand-waving.

We also prioritized We built a secure deployment flow with policy checks and GitOps to reduce manual `kubectl` errors and outages. and The platform is observability-first: metrics, alerts, and a dashboard keep the team ahead of deployment risk. so the architecture is built around real operational signal, not just feature scope.

See `docs/architecture/ADR-001-runtime-choice.md`

## Components

- go service with health, readiness, and domain-specific endpoints for Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.
- Prometheus metrics and structured logging for operators
- Docker image with non-root runtime and secure defaults
- K8s Deployment + HPA 2-10, 70% CPU
- GitOps (FluxCD) and rollback scripts
- The operational stack implied by the project: Go, Argo Rollouts, Crossplane, Terraform, Vault, OTel, Prometheus, Multi-cluster

## Trade-offs

| Choice | Why | Cost |
|---|---|---|
| K8s over serverless | team expertise, portability, predictable ops | more YAML |
| Self-hosted observability | lower cost than SaaS alternatives | we run it |
| RollingUpdate first | simpler for v0.1, canary later | faster shipping |

## Data flow

```
Client -> Ingress -> Service -> Pod
Pod -> /metrics -> Prometheus -> Alertmanager -> Slack
Domain actions -> API -> logs/metrics -> operators
```

## Scaling

HPA 2-10 pods. Stateless. 50m/64Mi request.

## Why not...

- **Serverless?** Cold start would hurt the main user flow and violate the reliability target.
- **Managed SaaS only?** The project must remain cost-effective and under operational control.
