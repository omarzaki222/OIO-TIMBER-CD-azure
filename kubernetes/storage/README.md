# Storage (Azure / AKS)

PostgreSQL uses a StatefulSet `volumeClaimTemplates` entry (`10Gi`, `ReadWriteOnce`).

No separate PVC manifest is required. On AKS, omit `storageClassName` so the
**default** StorageClass (typically Azure Disk CSI / `managed-csi`) binds the volume.

Do **not** use on-prem `local-path`. Do **not** use Azure Database for PostgreSQL in this lab.
