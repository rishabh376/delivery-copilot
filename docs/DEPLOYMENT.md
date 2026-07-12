# Deployment - delivery-copilot

**Use case:** Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.

## Infra requirements
→ `terraform/INFRA_REQUIREMENTS.md` - CPU/RAM/storage/network/cost breakdown

## GitOps
Flux watches `main` and reconciles changes automatically.

## Rollback
```
./scripts/rollback.sh
kubectl rollout undo deploy/delivery-copilot -n delivery-copilot
```
Usually < 30 sec.

## Cost
Cloudflare - $0/mo

We built a secure deployment flow with policy checks and GitOps to reduce manual `kubectl` errors and outages.
