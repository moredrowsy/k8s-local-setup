# Local Kubernetes Setup

This setup guide serves as a note for myself.

Kubernes, `k8s`, can be setup using different implementations:

- minikube
- kind
- k3s
- k3d (wrapper for k3s)

This setup guide will use `k3s` for single cluster or with `k3d` to create
multiple clusters and preserve states in each cluster.

## Requirements

- docker
- kubectl
- helm
- k3d

## k3s for Single Cluster

If you only need a single cluster then you only need to install `k3s`

### Install k3s

```shell
curl -sfL https://get.k3s.io | sh -
```

Without Traefik Ingress Controller

```shell
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--disable traefik" sh -
```

### Uninstall k3s

```shell
/usr/local/bin/k3s-uninstall.sh
```

## k3d

We can install multiple `k3s` clusters using `k3d`. Why?
Differrent ingress implemention have conflicts with each other.
We can install differrent ingress per cluster to test out each of them.

### Install k3d

```shell
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

### Installation by Ingress

Refer to the subfolders for each:

- istio
- nginx (by kubernetes.github.io)
- traefik

NOTE: Remember to stop other clusters when creating/using one to prevent
conflicts.

### k3d Useful Commands

Manager for k3s to install multiple clusters

To list K3s clusters

`k3d cluster list`

To stop a running cluster

`k3d cluster stop <cluster-name>`

To start a stopped cluster

`k3d cluster start <cluster-name>`

To delete a cluster

`k3d cluster delete <cluster-name>`
