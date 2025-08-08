# 🛠️ Task: Update Existing Kubernetes Deployment and Service

The Nautilus application development team has introduced new features that require updating the currently deployed application on the Kubernetes cluster. Your task is to **modify the existing deployment and service configuration** without deleting any existing resources.

## 🔍 Existing Setup

- **Deployment Name:** `nginx-deployment`
- **Service Name:** `nginx-service`

## ✅ Requirements

1. **Update the Service NodePort**
    - Change the `NodePort` of the service from `30008` to `32165`.

2. **Scale the Deployment**
    - Increase the number of replicas from `1` to `5`.

3. **Update the Container Image**
    - Change the image from `nginx:1.18` to `nginx:latest`.

> ⚠️ You are **not allowed to delete** the existing deployment or service. Updates must be done via `kubectl` or configuration editing.

## Hints

- You can use `kubectl patch`, `kubectl scale`, or `kubectl set image` for direct updates.
- Alternatively, export the current YAML configuration, edit the required fields, and re-apply it using `kubectl apply`.

## 🧪 Verification

After applying the changes, verify them using:

```bash
kubectl get deployment nginx-deployment
kubectl describe service nginx-service
kubectl get pods -l app=nginx
