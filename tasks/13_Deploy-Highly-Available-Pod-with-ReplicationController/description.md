# ✅ Task: Create a ReplicationController in Kubernetes

## 📘 Description

The **Nautilus DevOps team** is establishing a `ReplicationController` \
to ensure high availability for applications\
by deploying multiple pod replicas.

You are required to create a `ReplicationController` to manage the desired number of pods \
and maintain their availability as specified.

---

## 📋 Specifications

- **Kind**: ReplicationController
- **Name**: `nginx-replicationcontroller`
- **Image**: `nginx:latest`
- **Replica Count**: `3`

### 🔖 Labels (at pod level)
- `app: nginx_app`
- `type: front-end`

### 📦 Container Details
- **Name**: `nginx-container`

---

## ✅ Success Criteria

- A ReplicationController named `nginx-replicationcontroller` is created successfully.
- Exactly **3 pods** are running and managed by the controller.
- All pods are in `Running` state.
- Labels and container names are applied as specified.

---

## 🛠️ Helpful Commands

```bash
# Create the ReplicationController from a YAML file
kubectl apply -f nginx-replicationcontroller.yaml

# Verify pods are running
kubectl get pods -l app=nginx_app

# Check ReplicationController status
kubectl get rc nginx-replicationcontroller
