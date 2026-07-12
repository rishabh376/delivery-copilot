# Setup - delivery-copilot

Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.

1. **Infra first**: `cd terraform && terraform init && terraform apply`
2. `kubectl apply -k k8s/ -n delivery-copilot`
3. `kubectl port-forward svc/delivery-copilot 8080:80 -n delivery-copilot`
4. `curl localhost:8080/healthz`

Env vars: `PORT=8080`, `LOG_LEVEL=info`

The platform is observability-first: metrics, alerts, and a dashboard keep the team ahead of deployment risk.
