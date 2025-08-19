# Description for 02_Deploy_Lamp_Stack_on_Kubernetes_Cluster
Here’s the **full description in a single Markdown block** you can copy directly:

````markdown
# 🚀 Deploy a PHP Website on Kubernetes with Apache & MySQL

The Nautilus DevOps team needs to deploy a PHP website using **Apache (PHP)** as the web server and **MySQL** as the database on a Kubernetes cluster. Below are the requirements:

---

## 1. ConfigMap
- Create a **ConfigMap** named `php-config`.
- It must include `php.ini` with the following setting:
  ```ini
  variables_order = "EGPCS"
````

---

## 2. Deployment

* Create a **Deployment** named `lamp-wp`.
* It should have **two containers**:

    1. **httpd-php-container**

        * Image: `webdevops/php-apache:alpine-3-php7`
        * Mount the `php-config` ConfigMap at:

          ```
          /opt/docker/etc/php/php.ini
          ```
    2. **mysql-container**

        * Image: `mysql:5.6`

---

## 3. Secrets

* Create a **generic Kubernetes Secret** with the following keys:

    * `MYSQL_ROOT_PASSWORD`
    * `MYSQL_DATABASE`
    * `MYSQL_USER`
    * `MYSQL_PASSWORD`
    * `MYSQL_HOST`
* Use any values of your choice.
* Reference these secrets as environment variables inside both containers.
* **Note:** Use the `env` field (not `envFrom`) to define name-value pairs.

---

## 4. Services

1. **lamp-service**

    * Type: `NodePort`
    * Exposes the Apache container
    * `nodePort`: **30008**
2. **mysql-service**

    * Type: `ClusterIP` (default)
    * Exposes MySQL on port **3306**

---

## 5. Application File

* The file `/tmp/index.php` is present on the jump host.
* Copy it into the Apache container at:

  ```
  /app
  ```

* In the file, **do not hardcode MySQL values**.
  Instead, replace them with the **environment variables** you defined earlier:

    * `MYSQL_ROOT_PASSWORD`
    * `MYSQL_DATABASE`
    * `MYSQL_USER`
    * `MYSQL_PASSWORD`
    * `MYSQL_HOST`

---

## 6. Validation

* Access the application at:

  ```
  http://<NodeIP>:30008/index.php
  ```
* If configured correctly, it should display:

  ```
  Connected successfully
  ```
