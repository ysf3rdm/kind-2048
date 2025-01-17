# Deploy 2048 Game on Local Kubernetes Cluster with KIND

This repository provides all the resources and instructions needed to deploy the 2048 game on a local Kubernetes cluster using KIND (Kubernetes In Docker). Follow the guide below to set up your environment and access the application in your web browser.

## Installation and Deployment Guide 

### 1. Install KIND on Windows

1. Ensure Docker Desktop is installed and running.
2. Download the KIND binary:
   - Open PowerShell and run the following commands:
     ```powershell
     curl -Lo ./kind.exe https://kind.sigs.k8s.io/dl/v0.20.0/kind-windows-amd64
     ```
   - Move `kind.exe` to a directory in your `PATH`. For example:
     ```powershell
     move kind.exe C:\Windows\System32
     ```
3. Verify the installation:
   ```powershell
   kind version


### 2. Create KIND Cluster

1. Create a Kubernetes cluster using KIND:
```powershell
     kind create cluster
```
2. Verify the cluster is running:

```powershell
     kubectl cluster-info --context kind-kind
```

### 3. Pull 2048 Game From Docker
1. Pull the 2048 game Docker image from Docker Hub:
```powershell
    docker pull evilroot/docker-2048
```
2. Load Image into KIND cluster
```powershell
    kind load docker-image evilroot/docker-2048:latest
```
### 4. Deploy 2048 Game to Kubernetes

1. Apply the Kubernetes manifests to deploy the 2048 game
```powershell
    kubectl apply -f deployment.yml service.yml
```
2. Verify Deployment
```powershell
    kubectl get pods
```
### 5. Access the 2048 Game in Your Browser

1. Use the kubectl port-forward command to expose the service locally:
```powershell
    kubectl port-forward svc/service-2048 8080:80
```
2. Open your browser and navigate to > http://localhost:8080
