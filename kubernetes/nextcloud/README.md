```bash
$ helm repo add nextcloud https://nextcloud.github.io/helm/
$ helm repo update

$ helm install -f helm-values.yaml nextcloud-release nextcloud/nextcloud
```

```bash
$ helm delete nextcloud-release
```