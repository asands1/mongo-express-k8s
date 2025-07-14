# MongoDB + Mongo Express on Kubernetes

This project deploys MongoDB and Mongo Express on a local Kubernetes cluster using Minikube.

## 🔧 Files
- `mongodb-deployment.yaml` – MongoDB deployment + service
- `mongo-express.yaml` – Mongo Express deployment + LoadBalancer service
- `mongo-configmap.yaml` – Sets MongoDB hostname
- `mongodb-secret.yaml` – Encodes database credentials

## 🚀 Usage

```bash
minikube start
kubectl apply -f manifests/mongodb-secret.yaml
kubectl apply -f manifests/mongo-configmap.yaml
kubectl apply -f manifests/mongodb-deployment.yaml
kubectl apply -f manifests/mongo-express.yaml
minikube tunnel
minikube service mongodb-express-service --url