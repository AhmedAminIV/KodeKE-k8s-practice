## 📄 Task Description

The Nautilus DevOps team needs to set up a **Jenkins CI server** on a Kubernetes cluster to manage deployment pipelines for upcoming projects.

**Requirements:**

1. **Namespace**
    - Create a namespace named `jenkins`.

2. **Service**
    - Name: `jenkins-service`
    - Namespace: `jenkins`
    - Type: `NodePort`
    - NodePort: `30008`

3. **Deployment**
    - Name: `jenkins-deployment`
    - Namespace: `jenkins`
    - Labels: `app=jenkins`
    - Container name: `jenkins-container`
    - Image: `jenkins/jenkins`
    - ContainerPort: `8080`
    - Replicas: `1`

**Verification:**
- Wait until the Pod is in **Running** state.
- Access Jenkins login page in t
