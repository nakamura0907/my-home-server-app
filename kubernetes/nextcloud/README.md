```bash
helm repo add nextcloud https://nextcloud.github.io/helm/
helm install -f helm-values.yaml nextcloud-release nextcloud/nextcloud
```

```bash
helm delete nextcloud-release
```