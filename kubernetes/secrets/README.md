# Secrets (not applied from Git)

Real credentials are **never** committed. Before the first AKS deploy:

1. Create `oio-postgres` (`POSTGRES_DB`, `POSTGRES_USER`, `POSTGRES_PASSWORD`).
2. Create `oio-app-secrets` (`JWT_SECRET`, full `DATABASE_URL`).

See `secrets.example.yaml` for key names only.

Manifests reference these Secret names; they are **not** listed in `kustomization.yaml`.
