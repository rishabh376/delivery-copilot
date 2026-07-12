# Security - delivery-copilot

What we do:
- Trivy scan in CI - blocks HIGH/CRITICAL
- Cosign sign images
- Non-root UID 10001, readOnlyRootFilesystem
- NetworkPolicy default-deny
- RBAC least-privilege
- Secrets via External Secrets / Vault (not in git)
- Dependabot + CodeQL on

Threat model: Teams still fight slow manual work, unclear ownership, and brittle handoffs when delivery is under pressure.

We built a secure deployment flow with policy checks and GitOps to reduce manual `kubectl` errors and outages.
