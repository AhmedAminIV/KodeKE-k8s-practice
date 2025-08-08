# Kubernetes Sidecar Logging Pattern — Webserver with Log Shipper

## Overview
This task demonstrates the **Sidecar container pattern** in Kubernetes by running an Nginx web server alongside a log shipping container in the same Pod. The Nginx container focuses solely on serving web pages, while the sidecar container continuously reads and outputs Nginx's access and error logs for monitoring.

Since both containers share the same **emptyDir** volume, logs written by Nginx become immediately available to the sidecar container without persisting them beyond the Pod’s lifecycle.

---

## Requirements

1. **Pod Name:** `webserver`
2. **Volume:** `shared-logs` (type: `emptyDir`)
3. **Containers:**
   - **nginx-container**
      - Image: `nginx:latest`
      - Mounts `shared-logs` at `/var/log/nginx`
   - **sidecar-container**
      - Image: `ubuntu:latest`
      - Command:
        ```bash
        sh -c "while true; do cat /var/log/nginx/access.log /var/log/nginx/error.log; sleep 30; done"
        ```
      - Mounts `shared-logs` at `/var/log/nginx`

4. **Behavior:**
   - Nginx writes access and error logs to `/var/log/nginx` (inside the shared volume).
   - Sidecar container tails and prints logs to stdout every 30 seconds.
   - No persistent volume is used; logs exist only for the Pod’s lifetime.

---

## Benefits of the Sidecar Pattern
- **Separation of concerns:** Each container focuses on a single responsibility.
- **Scalability:** The log shipper can be replaced or updated without affecting the Nginx server.
- **Loose coupling:** Containers communicate only via the shared volume.

---

## Verification Steps
1. Deploy the Pod:
   ```bash
   kubectl apply -f webserver.yaml
