# n8n app architecture

## Ownership boundary

This repo owns the n8n workload itself.

The cluster-config repo owns the tenancy and security controls around this workload.

## Objects in this repo

- `Deployment` for the n8n service
- `Service` for in-cluster access

## Objects intentionally not here

- `Namespace`
- `Ingress`
- `NetworkPolicy`
- `PersistentVolumeClaim`
- `ResourceQuota`
- `LimitRange`

## Why this matters

Storage is intentionally kept in the trusted cluster-config repo along with the rest of the namespace guardrails.

If you later need secrets, external databases, or broader egress rules, expand those from the trusted repo after review instead of bypassing the boundary here.
