# data-platform-configs
ConfigMaps and ExternalSecrets for the data platform. Applied to the cluster via ArgoCD. Secrets are pulled from Infisical using the `infisical-store` ClusterSecretStore.

```
data-platform-configs/
│
├── README.md
│
├── infrastructure/
│   └── external-secrets/
│       └── infisical-store.yaml        ← ClusterSecretStore (Infisical backend)
│
└── apps/
    ├── argocd/
    │   ├── github-creds.yaml           ← ExternalSecret: GitHub repo credentials
    │   ├── ghcr-creds.yaml             ← ExternalSecret: GHCR OCI chart credentials
    │   └── image-updater-secret.yaml   ← ExternalSecret: ArgoCD Image Updater git token
    │
    ├── cert-manager/
    │   ├── clusterissuer.yaml          ← ClusterIssuer: letsencrypt-cloudflare
    │   └── cloudflare-secret.yaml      ← ExternalSecret: Cloudflare API token
    │
    └── hello-cicd/
        └── ghcr-pull-secret.yaml       ← ExternalSecret: GHCR image pull secret
```

## Infisical secrets required
| Key | Used by |
|---|---|
| `GITHUB_USERNAME` | ArgoCD repo creds, GHCR chart creds, image pull secret, image updater |
| `GITHUB_TOKEN` | ArgoCD repo creds, GHCR chart creds, image pull secret, image updater |
