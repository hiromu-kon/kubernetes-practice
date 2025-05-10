# Minikube + Argo CD Sample

## 🚀 Setup Minikube & Argo CD

```bash
# 1. Start Minikube
minikube start

# 2. Install Argo CD
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# 3. Confirm Argo CD is running
kubectl get pods -n argocd
```

## 🔐 Access the Argo CD Dashboard (HTTPS)

```bash
# 1. Port forward Argo CD server
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## 🔑 Argo CD Login Credentials
```bash
kubectl -n argocd get secret argocd-initial-admin-secret \
  -o jsonpath="{.data.password}" | base64 -d && echo
```

## 🧹 Clean Up

```bash
kubectl delete -f argocd/app-hello.yaml

kubectl delete -f hello-minikube/kubernetes/

kubectl delete namespace argocd
```