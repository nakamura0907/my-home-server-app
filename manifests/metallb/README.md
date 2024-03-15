```bash
$ helm repo add metallb https://metallb.github.io/metallb

$ kubectl create ns metallb-system
$ helm install metallb metallb/metallb --namespace metallb-system
```