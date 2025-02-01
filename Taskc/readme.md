# Kubernetes Webserver Deployment

## Overview
This project demonstrates the process of deploying a simple web server (Nginx) on a Kubernetes cluster using Minikube. The web server runs on port `3001` and is exposed via a Kubernetes Service.

## Prerequisites
Before starting, ensure you have the following installed:
- **Minikube**: A tool for running Kubernetes clusters locally.
- **kubectl**: The Kubernetes command-line tool for interacting with the cluster

## Installation

### 1. Install Minikube

I am using the Windows operating system:

### 2. Start Minikube

Initialize the Kubernetes cluster locally:
```bash
minikube start
```

## Deployment

### 1. Create the Deployment Configuration

Create a file called `webserver-deployment.yaml` with the following content:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webserver
spec:
  replicas: 1
  selector:
    matchLabels:
      app: webserver
  template:
    metadata:
      labels:
        app: webserver
    spec:
      containers:
      - name: webserver
        image: nginx:latest
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: webserver-service
spec:
  selector:
    app: webserver
  ports:
  - protocol: TCP
    port: 3001
    targetPort: 80
  type: LoadBalancer
```

### 2. Deploy the Web Server

Apply the configuration to your Kubernetes cluster:
```bash
kubectl apply -f webserver-deployment.yaml
```

### 3. Access the Web Server

Open the service in your browser:
```bash
minikube service webserver-service
```

This will open the Nginx web server running on port `3001`.