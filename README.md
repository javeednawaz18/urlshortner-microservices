# URL Shortener Microservices Platform

## Overview

This project demonstrates a microservices-based URL Shortener platform deployed on Kubernetes.

### Technology Stack

- Go
- Python
- Node.js
- Redis
- Docker
- Kubernetes
- Horizontal Pod Autoscaler (HPA)

---

## Project Structure

```text
go-service/
python-service/
node-service/
k8s/
docker-compose.yml
README.md
```

---

## Docker Deployment

### Clone Repository

```bash
git clone https://github.com/javeednawaz18/urlshortner-microservices.git

cd urlshortner-microservices
```

### Build and Run Containers

```bash
docker-compose up -d --build
```

### Verify Containers

```bash
docker ps -a
```

---

## Kubernetes Deployment

### Create Namespace

```bash
kubectl apply -f k8s/namespace.yaml
```

### Deploy All Kubernetes Resources

```bash
kubectl apply -f k8s/
```

### Verify Deployment

```bash
kubectl get pods -n urlshortener
```

```bash
kubectl get svc -n urlshortener
```

---

## ConfigMap Verification

```bash
kubectl get configmap -n urlshortener
```

---

## Secret Verification

```bash
kubectl get secret -n urlshortener
```

---

## Ingress Verification

```bash
kubectl get ingress -n urlshortener
```

---

## HPA Verification

```bash
kubectl get hpa -n urlshortener
```

---

## Final Verification

```bash
kubectl get all -n urlshortener
```

---

## Architecture

```text
                User
                  │
                  ▼
              Ingress
                  │
     ┌────────────┼────────────┐
     │            │            │
     ▼            ▼            ▼
Go Service   Python Service   Node Service
     │            │            │
     └────────────┼────────────┘
                  │
                  ▼
                Redis

                  │
                  ▼
            Kubernetes

      ┌───────────┴───────────┐
      ▼                       ▼
   ConfigMap                Secret
      ▼                       ▼
        HPA (Auto Scaling)

      ▼
Prometheus (Monitoring)
      ▼
Grafana (Dashboard)
```

---

## Monitoring

Prometheus and Grafana monitoring stack deployment was attempted using Helm.

### Helm Repository

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo update
```

### Chart

```text
kube-prometheus-stack
```

### Namespace

```text
monitoring
```

---

## Author

**Javeed Nawaz**
