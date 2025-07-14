# MongoDB + Mongo Express on Kubernetes

This project deploys MongoDB and Mongo Express on a local Kubernetes cluster using Minikube.

## 🔧 Files
- `mongodb-deployment.yaml` – MongoDB deployment + service
- `mongo-express.yaml` – Mongo Express deployment + LoadBalancer service
- `mongo-configmap.yaml` – Sets MongoDB hostname
- `mongodb-secret.yaml` – Encodes database credentials

## 🚀 Usage


You need to enter this in terminal in this order:

minikube start #Starts and runs minikube
kubectl apply -f manifests/mongodb-secret.yaml #applies the configuration files
kubectl apply -f manifests/mongo-configmap.yaml
kubectl apply -f manifests/mongodb-deployment.yaml
kubectl apply -f manifests/mongo-express.yaml
minikube tunnel #Leave this running in terminal, it starts a tunnel

Start a new terminal:

minikube service mongodb-express-service --url #this will give you an IP:port. Copy + Paste into your browser

Next: You will get a prompt for username and password. 

After that you will have access to Mongo-express and you create a db
