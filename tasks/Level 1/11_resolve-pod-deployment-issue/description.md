## 📝 Task Description

There is a Pod named `webserver` in the cluster. The pod contains **two containers**:

- **Main container**
    - Name: `httpd-container`
    - Image: `httpd:latest`

- **Sidecar container**
    - Name: `sidecar-container`
    - Image: `ubuntu:latest`

---

## 🔧 Objective

1. Investigate why the `webserver` pod is not in a **Running** state.
2. Apply the required fix so that the pod reaches the **Running** state successfully.

---

## 🧩 Notes

- Use `kubectl describe pod webserver` and `kubectl logs` to troubleshoot the issue.
- You can create a manifest file of running pod for faster modification using:  
```bash
kubectl get pod webserver -o yaml > pod.yaml
```

- Common issues include:
    - Missing command for Ubuntu container (it exits immediately).
    - ImagePull errors.
    - Misconfigured spec.

> ☑ Ensure both containers are healthy and the pod is in `Running` state before clicking **Finish**.

---
