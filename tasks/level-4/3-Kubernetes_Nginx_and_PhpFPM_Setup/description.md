We need to deploy a **php-based application** using **Nginx + PHP-FPM** with the following setup:

1. **Service**
    - Type: `NodePort`
    - NodePort: `30012`
    - Exposes the app.

2. **ConfigMap (`nginx-config`)**
    - Custom `nginx.conf`:
        - Change listen port → `8093`
        - Change root → `/var/www/html`
        - Change index → `index index.html index.htm index.php`

3. **Pod (`nginx-phpfpm`)**
    - Volumes:
        - `shared-files` (emptyDir) → mounted in both containers at `/var/www/html`.
        - `nginx-config-volume` (from ConfigMap) → mounted at `/etc/nginx/nginx.conf` using `subPath: nginx.conf`.
    - Containers:
        - **nginx-container**
            - Image: `nginx:latest`
            - Mounts `shared-files` at `/var/www/html`
            - Mounts `nginx-config-volume` at `/etc/nginx/nginx.conf`
        - **php-fpm-container**
            - Image: `php:8.1-fpm-alpine`
            - Mounts `shared-files` at `/var/www/html`

4. **Post-deploy**
    - Copy `/opt/index.php` from the jump host into `/var/www/html` inside the nginx container.
    - Access app via NodePort: `30012`.
