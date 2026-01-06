# 🚀 Kubernetes WebApp Deployment on AWS EC2
**A full-stack deployment using Minikube, MongoDB, and Nginx.**

---

## 🏗️ Architecture Overview
This project demonstrates a containerized web application deployed on a local Kubernetes cluster (Minikube) hosted on an AWS EC2 instance. 

- **Frontend/API:** Nginx-based Webapp
- **Database:** MongoDB
- **Infrastructure:** Minikube (Docker Driver)
- **Instance:** AWS EC2 (ec2-user)

---

## 🛠️ Deployment Manifests
The deployment is managed via four modular YAML files:
1. `configmap.yaml` - Environment variables and DB hosts.
2. `secrets.yaml` - Base64 encoded MongoDB credentials (template provided).
3. `db-deployment.yaml` - MongoDB Deployment and internal ClusterIP Service.
4. `webapp-deployment.yaml` - Webapp Deployment and NodePort Service.

---

## 🚀 Execution Steps

### 1. Environment Setup
The EC2 instance was prepared with Docker and Minikube.
```bash
minikube start --driver=docker
**Resources were applied in order of dependency:**
```bash
kubectl apply -f k8s/configmap.yaml
kubectl apply -f k8s/secrets.yaml
kubectl apply -f k8s/db-deployment.yaml
kubectl apply -f k8s/webapp-deployment.yaml

Verify that all pods are running and services are mapped correctly:
```bash
kubectl get all

