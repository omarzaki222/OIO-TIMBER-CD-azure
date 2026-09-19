# Argo CD (Azure)

## Application

`application.yaml` defines Application `oio-wood-timber-azure`:

| Field | Value |
|-------|--------|
| repoURL | `https://github.com/omarzaki222/OIO-TIMBER-CD-azure.git` |
| path | `environments/azure` |
| destination namespace | `oio-wood-timber` |

Argo CD **syncs desired state only**. It does not build images or push Git.

## Apply order

1. Terraform applies `helm_release.argocd`
2. Ensure CD Git repo is reachable (public or Argo repo credentials)
3. `kubectl apply -f CD/argocd/application.yaml` (or commit it into the CD repo and bootstrap)

## CD repo layout expected by path `environments/azure`

```text
kubernetes/
environments/azure/
argocd/
```

(When publishing from this monorepo, publish the contents of `CD/` as the CD repo root.)
