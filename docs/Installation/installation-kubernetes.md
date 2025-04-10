---
sidebar_label: Kubernetes
title: Kubernetes
slug: /installation/kubernetes
---

# Installing Strøm on Kubernetes using Helm

Strøm provides official Helm charts for deploying its core components to a Kubernetes cluster. This is the recommended installation method for production-like environments or when integrating with other Kubernetes-native systems.

The Helm charts are hosted in the [`stroem-hub/helm-charts`](https://github.com/stroem-hub/helm-charts) repository and include:
- `stroem-server`: The control plane and API layer
- `stroem-worker`: Distributed task execution units

> ✅ **Prerequisites**
>
> Before you begin, ensure you have:
>
> - Access to a running Kubernetes cluster (v1.22+ recommended)
> - [Helm 3.x](https://helm.sh/docs/intro/install/) installed locally
> - `kubectl` configured to access your cluster

---

## 🚀 Quickstart

To get Strøm server and worker up and running with default values:

```bash
# Add the Helm repository
helm repo add stroem https://stroem-hub.github.io/helm-charts

# Update the repo index
helm repo update

# Create a dedicated namespace
kubectl create namespace stroem

# Install the server component
helm install stroem-server stroem/stroem-server --namespace stroem

# Install the worker component
helm install stroem-worker stroem/stroem-worker --namespace stroem
```

This will deploy the core `server` and `worker` components into the `stroem` namespace using their default configurations.

---

## 🛠 Configuration

Each chart (`stroem-server` and `stroem-worker`) is independently configurable.
You can check [`stroem-server/values.yaml`](https://github.com/stroem-hub/helm-charts/blob/main/charts/stroem-server/values.yaml) and
[`stroem-worker/values.yaml`](https://github.com/stroem-hub/helm-charts/blob/main/charts/stroem-worker/values.yaml)
for details. 

---

## 🧹 Uninstalling

To completely remove Strøm from your cluster:

```bash
helm uninstall stroem-server --namespace stroem
helm uninstall stroem-worker --namespace stroem
kubectl delete namespace stroem
```

---

## 🐛 Need Help?

Check out the [stroem-hub/helm-charts](https://github.com/stroem-hub/helm-charts) repository for bug reports, contributions, and chart updates.

You can also join the conversation in [GitHub Discussions](https://github.com/stroem-hub/stroem/discussions) to ask questions or propose enhancements.

---
