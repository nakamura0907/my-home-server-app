```bash
$ helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
$ helm repo update

$ helm install -f helm-values.yaml ingress-release ingress-nginx/ingress-nginx
```

```bash
$ helm delete ingress-release
```