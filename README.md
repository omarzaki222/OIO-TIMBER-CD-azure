# CD — Continuous Delivery / GitOps (Azure)

```text
OIO-TIMBER-CD-azure (Git)
  → Argo CD
  → AKS
  → OIO Timber (frontend, backend, admin, postgres)
```

## Layout

| Path | Purpose |
|------|---------|
| `kubernetes/` | OIO app base manifests |
| `kubernetes/app-ingress/` | OIO frontend/API/admin Ingress (F5 NGINX / nip.io) |
| `kubernetes/platform-ingress/` | Jenkins, Argo CD, Grafana, Prometheus Ingress |
| `environments/azure/` | OIO app ACR image pins |
| `environments/platform/` | Platform Ingress kustomization entrypoint |
| `argocd/application.yaml` | Argo Application for OIO app |
| `argocd/application-platform.yaml` | Argo Application for platform Ingress |

## Git remote (CD repo)

`https://github.com/omarzaki222/OIO-TIMBER-CD-azure.git`

Publish the **contents** of this `CD/` directory as the CD repository root.

## Exposure

- App / Jenkins / Argo / monitoring Services stay **ClusterIP**
- One Azure LB: NGINX Ingress Service (`20.127.183.78`)
- Platform: `jenkins.`, `argocd.`, `grafana.`, `prometheus.` + `20.127.183.78.nip.io`
- OIO: `app.`, `api.`, `admin.` + `20.127.183.78.nip.io` (host-based; no path rewrite)

Bake frontend/admin with `NEXT_PUBLIC_API_URL=http://api.20.127.183.78.nip.io`.

## Secrets (out-of-band)

- `acr-auth` imagePullSecret in `oio-wood-timber`
- `oio-postgres`, `oio-app-secrets` (never in Git)
