## 🕒 Task 10: Set Up Time Check Pod in Kubernetes

The Nautilus DevOps team is experimenting with time-based logging\
and needs a temporary pod for testing.\
The objective is to create a pod that logs the current date every few seconds using a configurable interval.\
Below are the task details:

### ✅ Requirements:

- **Pod Name:** `time-check`
- **Namespace:** `nautilus`
- **Container Name:** `time-check`
- **Image:** `busybox:latest`
- **Command:**
  ```bash
  while true; do date >> /opt/security/time/time-check.log; sleep $TIME_FREQ; done
