# 🐳 MongoDB + Mongo Express on Kubernetes (Minikube)

This project deploys **MongoDB** and **Mongo Express** in a local Kubernetes cluster using **Minikube**.  
It’s ideal for testing a local database environment with a visual interface for interacting with MongoDB.

---




### ✅ 1. Prerequisites

Install the following tools:

| Tool             | macOS Download                                                                 | Windows Download                                                                  |
|------------------|----------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| **Git**          | [Git for macOS](https://git-scm.com/download/mac)                               | [Git for Windows](https://git-scm.com/download/win)                               |
| **Minikube**     | [Minikube for macOS](https://minikube.sigs.k8s.io/docs/start/#macos)            | [Minikube for Windows](https://minikube.sigs.k8s.io/docs/start/#windows)         |
| **kubectl**      | [kubectl for macOS](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/) | [kubectl for Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/) |
| **Docker Desktop** | [Docker for macOS](https://www.docker.com/products/docker-desktop/)           | [Docker for Windows](https://www.docker.com/products/docker-desktop/)            |
| **VS Code (optional)** | [VS Code](https://code.visualstudio.com/Download)                         | [VS Code](https://code.visualstudio.com/Download)                                 |

I use VS for editing YAML files, but it's optional!

---

## 🗂️ Project Structure

| File                      | Description                                        |
|---------------------------|----------------------------------------------------|
| `mongodb-deployment.yaml` | MongoDB deployment & service                       |
| `mongo-express.yaml`      | Mongo Express deployment & LoadBalancer service    |
| `mongo-configmap.yaml`    | ConfigMap for MongoDB hostname                     |
| `mongodb-secret.yaml`     | Secret for encoding MongoDB credentials            |


2. ## 🚀 Quick Start (macOS & Windows)

#in terminal

git clone https://github.com/asands1/mongo-express-k8s.git

cd mongo-express-k8s

---

## ⚙️ Usage Steps



### ✅ 1. Start Minikube

minikube start


---

### ✅ 2. Apply the Kubernetes YAML files
Make sure you're in the project root directory (pwd in terminal will give you the current working directory) Then run (in terminal):



kubectl apply -f manifests/mongodb-secret.yaml

kubectl apply -f manifests/mongo-configmap.yaml

kubectl apply -f manifests/mongodb-deployment.yaml

kubectl apply -f manifests/mongo-express.yaml


---

### ✅ 3. Start Minikube Tunnel
In a **new terminal window**, run:


minikube tunnel


> Keep this terminal open — it's required for accessing LoadBalancer services locally.

---

### ✅ 4. Access Mongo Express

In another terminal:


minikube service mongodb-express-service --url


This returns a URL like `http://12X.X.0.X:65XX`. Paste it into your browser.

---

### 🔐 Login Prompt

Use the credentials set in `mongodb-secret.yaml`.  
To retrieve and decode them:


kubectl get secret mongodb-secret -o yaml


Then decode each value:


echo <base64-value> | base64 --decode


---

## 🧪 You’re In!

Now you can:

- View MongoDB collections
- Create databases
- Insert, update, or delete documents via the web interface

---

## 🧼 To Tear It Down

kubectl delete -f manifests/
minikube stop


---


