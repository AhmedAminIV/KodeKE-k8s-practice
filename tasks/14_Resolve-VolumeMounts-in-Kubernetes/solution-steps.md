#### Fix Issue with VolumeMounts in Kubernetes

  1. Check the pod status,
  
  ```
  thor@jump_host ~$ kubectl get pods
  NAME           READY   STATUS    RESTARTS   AGE
  nginx-phpfpm   2/2     Running   0          63s
  ```
  
  2. Check the configmap,
  
  ```
  thor@jump_host ~$ kubectl get cm
  NAME           DATA   AGE
  nginx-config   1      68s
  ```
  
  3. Check the root directory path in configmap, note path is `/var/www/html` in configmap.
  
  ```
  thor@jump_host ~$ kubectl describe cm nginx-config
Name:         nginx-config
Namespace:    default
Labels:       <none>
Annotations:  <none>
  
  Data
  ====
nginx.conf:
  ----
  events {
}
  http {
  server {    listen 8099 default_server;
  listen [::]:8099 default_server;
  
  # Set nginx to serve files from the shared volume!
  root /var/www/html;
  index  index.html index.htm index.php;
  server_name _;
  location / {
  try_files $uri $uri/ =404;
  }
  location ~ \.php$ {
  include fastcgi_params;
  fastcgi_param REQUEST_METHOD $request_method;
  fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
  fastcgi_pass 127.0.0.1:9000;
  }
  }
}
  ```
  
  4. Now, check the mount path in a pod and edit the mountPath in the pod.yaml file to `/var/www/html`
  
  ```
  thor@jump_host ~$ kubectl get pod nginx-phpfpm -o yaml > pod.yaml
  
  Change mount path from /usr/share/nginx/html to /var/www/html
  ```
  
  5. Then delete and create a pod again,
  
  ```
  thor@jump_host ~$ kubectl delete pod nginx-phpfpm
  pod/nginx-phpfpm deleted
  
  thor@jump_host ~$ kubectl apply -f pod.yaml

  thor@jump_host ~$ kubectl get pods
  NAME           READY   STATUS    RESTARTS   AGE
  nginx-phpfpm   2/2     Running   0          7s
  ```
  
  
  6. Now, copy `index.php` from jump_host to container
```sh
  kubectl cp /home/thor/index.php nginx-phpfpm:/var/www/html -c nginx-container
```