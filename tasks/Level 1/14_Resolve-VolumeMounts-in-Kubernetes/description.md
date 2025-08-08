# Kubernetes Troubleshooting Task: Nginx & PHP-FPM Setup Issue

## 🧩 Task Description

The Nautilus DevOps team encountered an issue this morning\
with their **Nginx and PHP-FPM** application running on the Kubernetes cluster.\
The issue has caused the application to become non-functional\
and needs to be investigated and resolved.

You are required to:

---

### 🔍 Investigation

- A pod named: `nginx-phpfpm`
- A configmap named: `nginx-config`

Analyze the current state of the pod and its configuration\
to identify and fix the root cause of the malfunction.

---

### 🔧 Remediation Steps

1. **Inspect the Pod Logs**  
   Investigate the logs of the `nginx-phpfpm` pod to find error messages:
   ```bash
   kubectl logs nginx-phpfpm -c nginx-container
