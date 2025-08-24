# Description for 06_Environment_Variables_in_Kubernetes

## 📌 Scenario
Some applications require access to Pod and Node information through environment variables.
Kubernetes provides a way to automatically inject this data using the **`fieldRef`** mechanism.

In this task, we will create a Pod that prints out details about its environment\
such as node name, pod name, pod IP, and the service account name.

---

## 🎯 Task Requirements

1. **Pod**
    - Name: `envars`
    - Restart policy: `Never`

2. **Container**
    - Name: `fieldref-container`
    - Image: `busybox:latest`
    - Command: `sh -c`
    - Args:
      ```bash
      while true; do
        echo -en '\n';
        printenv NODE_NAME POD_NAME;
        printenv POD_IP POD_SERVICE_ACCOUNT;
        sleep 10;
      done;
      ```  

3. **Environment Variables (from fieldRef)**
    - `NODE_NAME` → `spec.nodeName`
    - `POD_NAME` → `metadata.name`
    - `POD_IP` → `status.podIP`
    - `POD_SERVICE_ACCOUNT` → `spec.serviceAccountName`

---

## 🔑 Key Concepts

- **fieldRef:** A Kubernetes feature that \
- allows you to expose Pod/Node metadata as environment variables.
- **printenv:** Command used to display environment variables inside the container.
- **Restart Policy = Never:** 
- Ensures the Pod doesn’t restart automatically after completion (useful for test/demo Pods).

---

## ✅ Expected Outcome

- A Pod named `envars` is created and running.
- When checking the logs or running `kubectl exec`, you will see the values for:
    - Node name
    - Pod name
    - Pod IP
    - Service account name  
