# Hello Minikube

This is a simple Go web server deployed on Kubernetes using Minikube.

## 🚀 Usage

```bash
# Use Minikube's Docker daemon
eval $(minikube docker-env)

# Build the Docker image inside Minikube
docker build -t hello-minikube .

# Apply Kubernetes manifests (Deployment and Service)
kubectl apply -f kubernetes/

# Access the service in your browser
minikube service hello-service

# (Optional) Port-forward the service to access it via http://localhost:8080
kubectl port-forward svc/hello-service 8080:80
```

## 🧹 Clean Up

```bash
# Delete all resources created from the manifest files
kubectl delete -f kubernetes/

kubectl delete deployment hello-deployment

docker build -t hello-minikube .

kubectl apply -f kubernetes/
```

## 📊 View the Dashboard

```bash
minikube dashboard
```
