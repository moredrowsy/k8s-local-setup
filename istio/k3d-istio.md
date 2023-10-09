# k3d

A wrapper for k3s

## Install

```shell
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

## Install k3s without traefik

Install k3s cluster

```shell
k3d cluster create istio --api-port 6550 --agents 1 --k3s-arg "--disable=traefik@server:0" --wait
```

## Install istio

```shell
helm repo add istio https://istio-release.storage.googleapis.com/charts
helm install istio-base istio/base -n istio-system --create-namespace  --set defaultRevision=default
helm install istiod istio/istiod -n istio-system --wait
helm install istio-ingress istio/gateway -n istio-ingress --create-namespace --set autoscaling.minReplicas=2 --wait
```

## Envoy injection for default [OPTIONAL]

```shell
kubectl patch namespace default -p '{ "metadata": { "labels": { "istio-injection": "enabled"  } }}'
```
