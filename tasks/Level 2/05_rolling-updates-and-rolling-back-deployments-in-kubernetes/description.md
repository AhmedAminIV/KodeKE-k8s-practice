## 📄 Task Description

The Nautilus DevOps team is preparing for a production deployment next week.  
They want to **test the deployment update and rollback** process in the **Dev environment**\
to identify risks in advance.

**Requirements:**

1. **Namespace**
    - Create a namespace named `devops`.

2. **Deployment**
    - Name: `httpd-deploy`
    - Namespace: `devops`
    - Container name: `httpd`
    - Image: `httpd:2.4.28`
    - Replicas: `4`
    - Strategy: `RollingUpdate`
        - `maxSurge`: `1`
        - `maxUnavailable`: `2`

3. **Service**
    - Name: `httpd-service`
    - Type: `NodePort`
    - NodePort: `30008`
    - Expose the deployment.

4. **Upgrade**
    - Update the deployment image to `httpd:2.4.43` using a **rolling update**.

5. **Rollback**
    - Once all pods are updated, **undo** the recent update and roll back to the previous/original version.
