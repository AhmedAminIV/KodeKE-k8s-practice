# Kubernetes Shared Volume - Task Description

The **Nautilus DevOps team** is developing a Kubernetes pod setup\
where two containers within a single pod share the same volume for temporary data exchange.\
Your goal is to replicate this scenario using a shared `emptyDir` volume.

---

## 📌 Objectives

1. **Create a pod** named `volume-share-devops`.

2. The pod should contain **two containers**:

   ### 🔹 Container 1:
    - **Image**: `debian:latest`
    - **Name**: `volume-container-devops-1`
    - **Command**: Run a `sleep` command to keep the container running
    - **Volume Mount**: Mount the shared volume at `/tmp/official`

   ### 🔹 Container 2:
    - **Image**: `debian:latest`
    - **Name**: `volume-container-devops-2`
    - **Command**: Run a `sleep` command to keep the container running
    - **Volume Mount**: Mount the shared volume at `/tmp/apps`

3. Define a **shared volume**:
    - **Name**: `volume-share`
    - **Type**: `emptyDir`

---

## ✅ Validation Steps

1. After deploying the pod, exec into the **first container**:

   ```bash
   kubectl exec -it volume-share-devops -c volume-container-devops-1 -- bash
