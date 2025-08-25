# Description for 07_Kubernetes_LEMP_Setup
# 🌐 Kubernetes LEMP Stack Deployment – Nautilus DevOps

## 📌 Scenario
The Nautilus DevOps team needs to deploy a **LEMP stack** (Linux, Nginx + PHP-FPM, MySQL)
in Kubernetes to host a static website. 
Sensitive database credentials must be stored securely in **Secrets**, 
PHP must be configured using a **ConfigMap**,
and the application should be exposed using a **NodePort service**.

---

## 🎯 Task Requirements

1. **Secrets**
    - `mysql-root-pass`
        - `password: R00t`
    - `mysql-user-pass`
        - `username: kodekloud_sam`
        - `password: TmPcZjtRQx`
    - `mysql-db-url`
        - `database: kodekloud_db1`
    - `mysql-host`
        - `host: mysql-service`

2. **ConfigMap**
    - Name: `php-config`
    - Key: `php.ini` with data:
      ```
      variables_order = "EGPCS"
      ```  

3. **Deployment**
    - Name: `lemp-wp`
    - Replicas: `1`
    - **Containers:**
        - `nginx-php-container`
            - Image: `webdevops/php-nginx:alpine-3-php7`
            - Mount `php-config` at `/opt/docker/etc/php/php.ini`
        - `mysql-container`
            - Image: `mysql:5.6`
    - **Environment Variables (explicit `env`)**:
        - `MYSQL_ROOT_PASSWORD` → from `mysql-root-pass:password`
        - `MYSQL_DATABASE` → from `mysql-db-url:database`
        - `MYSQL_USER` → from `mysql-user-pass:username`
        - `MYSQL_PASSWORD` → from `mysql-user-pass:password`
        - `MYSQL_HOST` → from `mysql-host:host`

4. **Services**
    - `lemp-service` → NodePort, port `80`, targetPort `80`, nodePort `30008`
    - `mysql-service` → ClusterIP, port `3306`

5. **Website Setup**
    - File `/tmp/index.php` must be copied into the container at `/app`.
    - In the PHP file, MySQL credentials should reference **environment variables**\
   (`$_ENV['MYSQL_*']`) instead of hard-coded values.
    - Expected output when accessing the service:
      ```
      Connected successfully
      ```  

---

## 🔑 Key Concepts

- **Secrets**: Store sensitive MySQL credentials.
- **ConfigMap**: Store PHP configuration (php.ini).
- **env (not envFrom)**: Explicit mapping of secret keys to environment variables.
- **NodePort Service**: Exposes Nginx on port `30008` externally.
- **ClusterIP Service**: Provides stable DNS name `mysql-service` for database access.

---

## ✅ Expected Outcome

- Deployment `lemp-wp` running with Nginx+PHP and MySQL containers.
- ConfigMap successfully mounted to PHP config path.
- Secrets injected as environment variables into both containers.
- Website accessible at `http://<NodeIP>:30008` showing:  
