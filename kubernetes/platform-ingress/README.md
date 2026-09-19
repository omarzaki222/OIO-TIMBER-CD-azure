# Platform Ingress (Jenkins + Argo CD + monitoring)

Host-based routes on the **existing** NGINX LoadBalancer IP `20.127.183.78`
(F5 NGINX Ingress Controller, IngressClass `nginx`).

| Host | Backend |
|------|---------|
| `jenkins.20.127.183.78.nip.io` | `jenkins/jenkins:8080` (HTTP + WebSocket) |
| `argocd.20.127.183.78.nip.io` | `argocd/argocd-server:80` (TLS to pod; `server.insecure=false`) |
| `grafana.20.127.183.78.nip.io` | `monitoring/monitoring-grafana:80` (HTTP + WebSocket) |
| `prometheus.20.127.183.78.nip.io` | `monitoring/monitoring-kube-prometheus-prometheus:9090` |

Deploy via Kustomize path `environments/platform`.
Do not change these Services to LoadBalancer.
