# Description for 04_Persistent_Volumes_in_Kubernetes
# 📦 Kubernetes Persistent Storage Practice – Nautilus DevOps

## 📌 Scenario
The Nautilus DevOps team needs to deploy a **web application**\
on Kubernetes with persistent storage for application code.\
To achieve this, they will use a **PersistentVolume (PV)**, **PersistentVolumeClaim (PVC)**,\
and connect them to a Pod running an **Apache HTTP server**.\
The application will also be exposed externally using a **NodePort service**.

This exercise demonstrates how Kubernetes manages storage resources and makes them available to Pods.

---

## 🎯 Task Requirements

1. **PersistentVolume (PV)**
    - Name: `pv-devops`
    - StorageClass: `manual`
    - Capacity: `3Gi`
    - Access Mode: `ReadWriteOnce`
    - Type: `hostPath`
    - Path: `/mnt/devops`

2. **PersistentVolumeClaim (PVC)**
    - Name: `pvc-devops`
    - StorageClass: `manual`
    - Request: `3Gi`
    - Access Mode: `ReadWriteOnce`

3. **Pod**
    - Name: `pod-devops`
    - Labels: `app=devops`
    - Container:
        - Name: `container-devops`
        - Image: `httpd:latest`
        - VolumeMount:
            - Claim: `pvc-devops`
            - Mount Path: `/usr/local/apache2/htdocs` (Apache document root)

4. **Service**
    - Name: `web-devops`
    - Type: `NodePort`
    - Selector: `app=devops`
    - Ports:
        - Port: `80`
        - TargetPort: `80`
        - NodePort: `30
