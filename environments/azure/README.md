# Azure environment (`CD/environments/azure`)

Kustomize overlay for AKS.

## Images

```text
oioazureregistry.azurecr.io/oio/backend:<tag>
oioazureregistry.azurecr.io/oio/frontend:<tag>
oioazureregistry.azurecr.io/oio/admin:<tag>
```

CI updates `newTag` and pushes this file to `OIO-TIMBER-CD-azure`.

## Pull secret

Deployments use `imagePullSecrets: [acr-auth]` (created out-of-band in namespace `oio-wood-timber`).

## Argo CD

Application `oio-wood-timber-azure` syncs path `environments/azure` from the CD Git repo.
