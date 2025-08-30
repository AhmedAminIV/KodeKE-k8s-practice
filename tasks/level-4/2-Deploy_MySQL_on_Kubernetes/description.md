# MySQL Deployment on Kubernetes

The Nautilus DevOps team needs to deploy a new **MySQL server** on the Kubernetes cluster
with persistent storage, secrets for credentials, and a NodePort service for access.

### Requirements

1. **Persistent Volume**
    - Name: `mysql-pv`
    - Capacity: `250Mi`

2. **Persistent Volume Claim**
    - Name: `mysql-pv-claim`
    - Request: `250Mi`

3. **Secrets**
    - `mysql-root-pass`
        - key: `password`, value: `YUIidhb667`
    - `mysql-user-pass`
        - key: `username`, value: `kodekloud_rin`
        - key: `password`, value: `8FmzjvFU6S`
    - `mysql-db-url`
        - key: `database`, value: `kodekloud_db5`

4. **Deployment**
    - Name: `mysql-deployment`
    - Image: `mysql:5.7` (or any MySQL version of choice)
    - Container name: `mysql`
    - Mount PVC at `/var/lib/mysql`
    - Environment variables (from secrets):
        - `MYSQL_ROOT_PASSWORD` → from `mysql-root-pass.password`
        - `MYSQL_DATABASE` → from `mysql-db-url.database`
        - `MYSQL_USER` → from `mysql-user-pass.username`
        - `MYSQL_PASSWORD` → from `mysql-user-pass.password`

5. **Service**
    - Name: `mysql`
    - Type: `NodePort`
    - Port: `3306`
    - NodePort: `30007`
