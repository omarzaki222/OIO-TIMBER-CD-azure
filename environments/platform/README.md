# Platform environment (Jenkins, Argo CD, Grafana, Prometheus Ingress)

Kustomize entrypoint for platform Ingress manifests.

```text
kubectl kustomize environments/platform
```

Argo CD Application: see `argocd/application-platform.yaml`.

Not part of `environments/azure` (OIO app).
