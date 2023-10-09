# k3d

A wrapper for k3s

## Install

```shell
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

## Install k3s without traefik

Install k3s cluster

```shell
k3d cluster create nginx --api-port 6550 --agents 1 --k3s-arg "--disable=traefik@server:0" --wait
```

## Install ingress-nginx

```shell
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install ingress-nginx ingress-nginx/ingress-nginx \
  --create-namespace \
  --set "controller.ingressClassResource.default=true" \
  --set "controller.watchIngressWithoutClass=true"
```
