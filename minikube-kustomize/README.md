# Minikube Kustomize Example

This is a simple example to learn how to use [Kustomize](https://kustomize.io/) with Minikube.

The structure uses a `base/` directory with common Kubernetes manifests, and an `overlays/dev/` directory to override them for a development environment.

---

## 📁 Directory Structure
minikube-kustomize/
  ├── base/
  │ ├── deployment.yaml
  │ ├── service.yaml
  │ └── kustomization.yaml
  └── overlays/
  └── dev/
  ├── patch-deployment.yaml
  └── kustomization.yaml

## 🚀 Usage

```bash
# 1. Start Minikube
minikube start

# 2. Enable metrics-server (optional, for autoscaling)
minikube addons enable metrics-server

# 3. Deploy with Kustomize
kubectl apply -k overlays/dev
kubectl apply -k overlays/stg

# 4. Verify Deployment
kubectl get deployments
kubectl get pods
kubectl get service hello-service

# 5. Access the app
minikube service hello-service
```