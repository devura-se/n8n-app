# Devura n8n App

This repository is an application repository for running n8n in the Devura cluster.

In your local workspace, this repo sits next to the bootstrap repo as `../devura-n8n-app`.

It owns reviewed workload-level resources for this app:

- `Deployment`
- `Service`

It does **not** own:

- namespace creation
- ingress exposure
- persistent volume claims
- quota/limits
- baseline network policies

Those are managed centrally from the trusted `devura-cluster-config` repository.

## Layout

```text
deploy/
  base/
  overlays/
    prod/
docs/
```

## What Argo CD should point at

Use:

- repo path: `deploy/overlays/prod`
- revision: `main`

## Runtime notes

The deployment mounts the trusted `n8n-data` persistent volume claim created from `devura-cluster-config` at `/home/node/.n8n`.

The image is currently pinned to `docker.n8n.io/n8nio/n8n:latest` so you can get started quickly. Pin an explicit version before treating this as production.
