## 📄 Task Description

The Nautilus DevOps team needs to deploy a **static website** using **Nginx** on a **Kubernetes cluster**.  
The goal is to make the application **highly available** and **scalable** by running multiple replicas.

**Requirements:**
1. **Deployment**
    - Name: `nginx-deployment`
    - Image: `nginx:latest`
    - Container name: `nginx-container`
    - Replicas: `3`
2. **Service**
    - Name: `nginx-service`
    - Type: `NodePort`
    - NodePort: `30011`
