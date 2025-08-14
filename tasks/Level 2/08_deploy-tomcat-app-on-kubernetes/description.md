## 📄 Task Description

A new Java-based application needs to be deployed on the Kubernetes cluster.  
The DevOps team will set up the **application stack** under the existing cluster as per the requirements.

**Requirements:**

1. **Namespace**
    - Name: `tomcat-namespace-devops`

2. **Deployment**
    - Name: `tomcat-deployment-devops`
    - Namespace: `tomcat-namespace-devops`
    - Replica count: `1`
    - Container name: `tomcat-container-devops`
    - Image: `gcr.io/kodekloud/centos-ssh-enabled:tomcat`
    - Container port: `8080`

3. **Service**
    - Name: `tomcat-service-devops`
    - Namespace: `tomcat-namespace-devops`
    - Type: `NodePort`
    - NodePort: `32227`

**Verification:**
- Wait until the Pod is in **Running** state.
- Access the Tomcat app in the browser via:
