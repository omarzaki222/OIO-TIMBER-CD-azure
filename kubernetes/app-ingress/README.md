# OIO application Ingress

Host-based routes on the **existing** NGINX LoadBalancer IP `20.127.183.78`
(F5 `nginx.org/ingress-controller`, `ingressClassName: nginx`).

| Host | Backend |
|------|---------|
| `app.20.127.183.78.nip.io` | `frontend:3000` |
| `api.20.127.183.78.nip.io` | `backend:8080` |
| `admin.20.127.183.78.nip.io` | `admin:3000` |

Bake `NEXT_PUBLIC_API_URL=http://api.20.127.183.78.nip.io` into frontend/admin images
(clients already append `/api/v1/...`). Set `CORS_ALLOWED_ORIGINS` to the app + admin origins.
