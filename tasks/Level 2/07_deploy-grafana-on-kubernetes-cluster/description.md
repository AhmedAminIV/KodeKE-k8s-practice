## 📄 Task Description

The Nautilus DevOps team is setting up **Grafana** on a Kubernetes cluster to collect and analyze application analytics.

**Requirements:**

1. **Deployment**
    - Name: `grafana-deployment-nautilus`
    - Use any official Grafana image (e.g., `grafana/grafana`)
    - Other parameters (labels, ports, replicas) can be chosen freely.

2. **Service**
    - Type: `NodePort`
    - NodePort: `32000`
    - Expose the Grafana application.

**Verification:**
- Wait until the Pod is in **Running** state.
- Access Grafana login page in the browser via:
