# Operations Runbook - delivery-copilot

Helps devops teams reduce toil around delivery with a guided workflow and measurable guardrails.

**On-call? Read this first.**

## Deploy
```
kubectl apply -k k8s/ -n delivery-copilot
kubectl rollout status deploy/delivery-copilot -n delivery-copilot
```

## Rollback (when things go red)
```
./scripts/rollback.sh
# usually < 30sec
```

## Scale up NOW
```
kubectl scale deploy/delivery-copilot --replicas=10 -n delivery-copilot
```

## Logs
```
kubectl logs -l app=delivery-copilot -n delivery-copilot -f --tail=200
```

## Crashloop?
```
kubectl describe pod -l app=delivery-copilot -n delivery-copilot
kubectl logs <pod> --previous -n delivery-copilot
```
90% of the time: missing env var in ConfigMap.

## Metrics
`curl localhost:8080/metrics` or Grafana dashboard in `monitoring/`

## DR / Failover
See `docs/DISASTER_RECOVERY.md` - RTO 15m

We actually tested this. 11 min.
