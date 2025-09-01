We’re deploying a fresh **Drupal application** on Kubernetes with a **MySQL backend**.

### Requirements Breakdown:

1. **Persistent Storage**

    * PV: `drupal-mysql-pv` → `hostPath=/drupal-mysql-data`, `size=5Gi`, `RWO`.
    * PVC: `drupal-mysql-pvc` → request `3Gi`, `RWO`.

2. **MySQL Deployment**

    * Name: `drupal-mysql`
    * Image: `mysql:5.7`
    * 1 replica
    * PVC mounted at `/var/lib/mysql`
    * Service: `drupal-mysql-service` → port `3306`.

3. **Drupal Deployment**

    * Name: `drupal`
    * Image: `drupal:8.6`
    * 1 replica
    * Service: `drupal-service` → NodePort `30095`.

4. **Secrets/Config**

    * Define MySQL root password, DB, user, etc. with Kubernetes `Secrets`.

5. **Expected Result**

    * Drupal installation page accessible from browser using the NodePort.

---