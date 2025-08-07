## 📋 Task Description

The Nautilus DevOps team has started experimenting with Pods and Services on the Kubernetes platform as part of their initiative to migrate most of their applications.

You have been assigned the following task:

> 🔧 **Create a Pod** with the specifications below:

- **Pod Name:** `pod-nginx`
- **Image:** `nginx:latest`
- **Container Name:** `nginx-container`
- **Labels:**
    - `app: nginx_app`

---

## 🧠 Notes

- ✅ Ensure the image **tag is explicitly set** as `nginx:latest`, even though it’s the default.
- 🛠️ Use `kubectl` either to apply a YAML manifest or create the pod directly via command-line.
- 🔐 The **jump_host** is already configured with `kubectl` to interact with the Kubernetes cluster.

---