# Microservices Deployment with Kubernetes on Minikube

## Overview
This project demonstrates the deployment of a microservices-based application using Docker containers and Kubernetes on a local Minikube cluster.

### Microservices
- Auth Service: Handles user authentication.
- Product Service: Manages product data.
- User Service: Manages user data.

### Prerequisites
- Minikube installed on your local machine.
- Kubernetes CLI (kubectl)
- Docker
- GitLab CI/CD (optional for CI/CD pipeline)
- Prometheus and Grafana (for monitoring)

### Steps to Deploy
1. **Start Minikube:**
   ```bash
   minikube start
2. **Enable ingress in Minikube:**
   minikube addons enable ingress
3. **Build Docker images:**
   docker build -t auth-service:latest auth-service/
   docker build -t product-service:latest product-service/
   docker build -t user-service:latest user-service/
3. **Deploy microservices, ingress and set up prometheus and grafana in K8s:**
   kubectl apply -f k8s/auth-deployment.yaml
   kubectl apply -f k8s/auth-service.yaml
   kubectl apply -f k8s/product-deployment.yaml
   kubectl apply -f k8s/product-service.yaml
   kubectl apply -f k8s/user-deployment.yaml
   kubectl apply -f k8s/user-service.yaml
   kubectl apply -f k8s/ingress.yaml
   kubectl apply -f k8s/prometheus-deployment.yaml
   kubectl apply -f k8s/grafana-deployment.yaml
4. **port-forward to expose grafana to port 3000:**
   kubectl port-forward deployment/grafana 3000:3000
5. **Configure logging with ELK stack:**
   kubectl apply -f k8s/elk-stack-deployment.yaml
6. **port-forward to be able to access to Kibana:**
   kubectl port-forward deployment/elk-stack 5601:5601
   Open a browser and go to: http://localhost:5601
7. **Clean cluster and stop minikube:**
   kubectl delete -f k8s/
   minikube stop






