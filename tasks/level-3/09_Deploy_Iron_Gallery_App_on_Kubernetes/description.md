# Description for 09_Deploy_Iron_Gallery_App_on_Kubernetes
## Iron Gallery & Iron DB Deployment Task

The Nautilus DevOps team needs to deploy two applications — **Iron Gallery** (frontend) and **Iron DB** (database) — inside a custom namespace. Below is the breakdown of what is required:

---

### 1. Namespace
- A namespace `iron-namespace-datacenter` is created to logically isolate the resources.

---

### 2. Iron Gallery Deployment
- **Name**: `iron-gallery-deployment-datacenter`
- **Namespace**: `iron-namespace-datacenter`
- **Labels**: `run=iron-gallery`
- **Replicas**: `1`
- **Container**:
    - Name: `iron-gallery-container-datacenter`
    - Image: `kodekloud/irongallery:2.0`
    - Resource Limits: `memory=100Mi`, `cpu=50m`
- **Volumes**:
    - `config`: Mounted at `/usr/share/nginx/html/data` using `emptyDir`
    - `images`: Mounted at `/usr/share/nginx/html/uploads` using `emptyDir`

---

### 3. Iron DB Deployment
- **Name**: `iron-db-deployment-datacenter`
- **Namespace**: `iron-namespace-datacenter`
- **Labels**: `db=mariadb`
- **Replicas**: `1`
- **Container**:
    - Name: `iron-db-container-datacenter`
    - Image: `kodekloud/irondb:2.0`
    - Environment Variables:
        - `MYSQL_DATABASE=database_host`
        - `MYSQL_ROOT_PASSWORD=<complex-password>`
        - `MYSQL_USER=<custom-user>` (not root)
        - `MYSQL_PASSWORD=<complex-password>`
    - Volume:
        - `db`: Mounted at `/var/lib/mysql` using `emptyDir`

---

### 4. Services
- **Iron DB Service**
    - Name: `iron-db-service-datacenter`
    - Type: `ClusterIP`
    - Selector: `db=mariadb`
    - Port: `3306` (TCP)
- **Iron Gallery Service**
    - Name: `iron-gallery-service-datacenter`
    - Type: `NodePort`
    - Selector: `run=iron-gallery`
    - Port: `80` → NodePort: `32678` (TCP)

---

✅ After applying the manifests, accessing the NodePort on any cluster node’s IP at port `32678` should display the Iron Gallery installation page. Database connection setup is **not required** at this stage.
