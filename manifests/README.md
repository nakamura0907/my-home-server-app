## kind

```bash
$ kind create cluster --config kubernetes/kind-config.yaml

$ kind delete cluster --name kind
```

## K3s

```bash
$ export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```

## Helm

```bash
$ helm show values \<chart\> > helm-values.yaml
```