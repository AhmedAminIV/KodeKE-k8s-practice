# Description for 03_Init_Containers_in_Kubernetes
## 📌 Scenario
Some applications require specific configurations or setup steps **before** the main application container runs.\
Since these changes cannot be baked directly into container images, \
the DevOps team at **xFusionCorp Industries** has decided to use **InitContainers**.

InitContainers run **before** the main container starts.\
They are perfect for preparing files, setting up environment dependencies, or running initialization logic.\
Once the InitContainer finishes successfully, Kubernetes will start the main container.

---

## 🎯 Task Requirements

1. **Create a Deployment**
    - Name: `ic-deploy-xfusion`
    - Replicas: `1`
    - Labels:
        - Deployment → `app=ic-xfusion`
        - Pod template → `app=ic-xfusion`

2. **InitContainer**
    - Name: `ic-msg-xfusion`
    - Image: `debian:latest`
    - Command:
      ```bash
      /bin/bash -c "echo Init Done - Welcome to xFusionCorp Industries > /ic/news"
      ```  
    - Volume Mount:
        - Name: `ic-volume-xfusion`
        - Mount Path: `/ic`

3. **Main Container**
    - Name: `ic-main-xfusion`
    - Image: `debian:latest`
    - Command:
      ```bash
      /bin/bash -c "while true; do cat /ic/news; sleep 5; done"
      ```  
    - Volume Mount:
        - Name: `ic-volume-xfusion`
        - Mount Path: `/ic`

4. **Volume**
    - Name: `ic-volume-xfusion`
    - Type: `emptyDir`

---

## 🔑 Key Concepts

- **InitContainers**
    - Run **once** before main containers.
    - Ensure preconditions are met before app starts.

- **emptyDir Volume**
    - Ephemeral storage that lives as long as the Pod runs.
    - Provides a **shared filesystem** between InitContainer and main container.

- **Data Flow in this Task**
    1. InitContainer writes a welcome message into `/ic/news`.
    2. Main container continuously reads and displays the file contents.

---

## ✅ Expected Outcome

- A running Deployment (`ic-deploy-xfusion`) with **1 replica**.
- Pod starts with an **InitContainer** → writes the message.
- Main container continuously **outputs the welcome message** to logs every 5 seconds.  
