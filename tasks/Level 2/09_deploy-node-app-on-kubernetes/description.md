## 📄 Task Description

The Nautilus development team has finished building a **Node.js application** and plans to deploy it on a Kubernetes cluster.  
The DevOps team will handle deployment and exposure of the app based on the following requirements.

**Requirements:**

1. **Deployment**
    - Image: `gcr.io/kodekloud/centos-ssh-enabled:node`
    - Replica count: `2`

2. **Service**
    - Type: `NodePort`
    - `targetPort`: `8080`
    - `nodePort`: `30012`

**Verification:**
- Ensure all Pods are in **Running** state.
- Access the app via the **NodeApp** button in the top bar or:
