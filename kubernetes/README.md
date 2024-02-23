## kind

```bash
$ kind create cluster --config kubernetes/kind-config.yaml

$ kind delte cluster --name kind
```

### Ingress

```bash
$ kubectl apply -f https://projectcontour.io/quickstart/contour.yaml
$ kubectl patch daemonsets -n projectcontour envoy -p '{"spec":{"template":{"spec":{"nodeSelector":{"ingress-ready":"true"},"tolerations":[{"key":"node-role.kubernetes.io/control-plane","operator":"Equal","effect":"NoSchedule"},{"key":"node-role.kubernetes.io/master","operator":"Equal","effect":"NoSchedule"}]}}}}'

$ kubectl apply -f https://raw.githubusercontent.com/Kong/kubernetes-ingress-controller/master/deploy/single/all-in-one-dbless.yaml
$ kubectl patch deployment -n kong proxy-kong -p '{"spec":{"replicas":1,"template":{"spec":{"containers":[{"name":"proxy","ports":[{"containerPort":8e3,"hostPort":80,"name":"proxy-tcp","protocol":"TCP"},{"containerPort":8443,"hostPort":443,"name":"proxy-ssl","protocol":"TCP"}]}],"nodeSelector":{"ingress-ready":"true"},"tolerations":[{"key":"node-role.kubernetes.io/control-plane","operator":"Equal","effect":"NoSchedule"},{"key":"node-role.kubernetes.io/master","operator":"Equal","effect":"NoSchedule"}]}}}}'
$ kubectl patch service -n kong kong-proxy -p '{"spec":{"type":"NodePort"}}'
$ kubectl patch ingress example-ingress -p '{"spec":{"ingressClassName":"kong"}}'

$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
$ kubectl wait --namespace ingress-nginx \
  --for=condition=ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=90s
```