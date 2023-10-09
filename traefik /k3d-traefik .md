# k3d

A wrapper for k3s

## Install

```shell
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

## Install k3s without traefik

Install k3s cluster

```shell
k3d cluster create traefik --api-port 6550 --agents 1 --wait
```
