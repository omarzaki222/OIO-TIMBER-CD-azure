# Platform Ingress (Jenkins + Argo CD)

Host-based routes on the **existing** NGINX LoadBalancer IP `20.253.224.52`
(F5 NGINX Ingress Controller, IngressClass `nginx`).

| Host | Backend |
|------|---------|
| `jenkins.20.253.224.52.nip.io` | `jenkins/jenkins:8080` (HTTP) |
| `argocd.20.253.224.52.nip.io` | `argocd/argocd-server:80` (TLS to pod; `server.insecure=false`) |

Deploy via Kustomize path `environments/platform` (or apply the Ingress YAMLs).
Do not change Jenkins/Argo Services to LoadBalancer.
