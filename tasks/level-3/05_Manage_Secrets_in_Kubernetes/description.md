# Description for 05_Manage_Secrets_in_Kubernetes

## 📌 Scenario
The Nautilus DevOps team is deploying licensed tools on Kubernetes.\
Since license keys and sensitive information must be stored securely,\
they have decided to use **Kubernetes Secrets**.\
Secrets allow confidential data such as passwords, tokens, or license numbers\
to be stored safely and consumed by Pods.

This task demonstrates how to create a secret from a file and mount it into a Pod.

---

## 🎯 Task Requirements

1. **Secret**
    - Name: `official`
    - Type: `generic`
    - Created from file: `/opt/official.txt` (contains the password/license number).

2. **Pod**
    - Name: `secret-datacenter`
    - Container:
        - Name: `secret-container-datacenter`
        - Image: `ubuntu:latest`
        - Command: `sleep 3600` (to keep the container running).
    - Mount secret:
        - Secret: `official`
        - Mount path: `/opt/games`

---

## 🔑 Key Concepts

- **Secrets**: Kubernetes objects for storing small amounts of sensitive data securely.
- **Mounting Secrets as Volumes**: Secrets can be injected into Pods as files under a specified path.
- **Verification**: By `kubectl exec` into the Pod,\
- the secret should appear under `/opt/games` inside the container.

---

## ✅ Expected Outcome

- A secret named `official` exists in the cluster containing the license key.
- A Pod named `secret-datacenter` is running with the secret mounted.
- Checking `/opt/games` inside the Pod should reveal the secret file with the correct license key.  
