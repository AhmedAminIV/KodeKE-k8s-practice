# Description for 10_Fix_Python_App_Deployed_on_Kubernetes_Cluster
## Python App Debugging & Fix

The Nautilus DevOps team deployed a Python Flask application,
but it failed to come up due to misconfiguration.

Here are the issues and fixes:

---

### 1. Deployment
- **Name**: `python-deployment-nautilus`
- **Image**: `poroko/flask-demo-appimage` (correct spelling must be ensured).
- **Container Port**: Flask default port is `5000`, so `containerPort` must be set to `5000`.

---

### 2. Service
- **Name**: `python-deployment-nautilus` (or the existing one).
- **Selector**: Must match the Deployment labels.
- **Type**: `NodePort`
- **Port Mapping**:
    - Port: `5000`
    - TargetPort: `5000` (Flask default)
    - NodePort: `32345`

---

✅ After fixing, the app will be accessible via any cluster node’s IP at port **32345**.
