# Description for 01_Deploy_Apache_Web_Server_on_Kubernetes_Cluster
## 🚀 Problem Description

We need to deploy an application on a Kubernetes cluster under **Apache Web Server**.  
The requirements are as follows:

1. Create a namespace named **`httpd-namespace-datacenter`**.
2. Create a deployment named **`httpd-deployment-datacenter`** under the newly created namespace.
    - Use image **`httpd:latest`** (must include the tag).
    - Replica count should be **2**.
3. Create a service named **`httpd-service-datacenter`** under the same namespace.
    - Service type: **NodePort**
    - NodePort: **30004**
    - Expose the deployment.

---