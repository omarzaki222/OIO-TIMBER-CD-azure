# Platform environment (Jenkins + Argo CD Ingress only)

Kustomize entrypoint for platform Ingress manifests.

```text
kubectl kustomize CD/environments/platform
```

Argo CD Application (optional bootstrap): see `CD/argocd/application-platform.yaml`.

Not part of `environments/azure` (OIO app).
