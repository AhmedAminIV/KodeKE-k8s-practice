# Guestbook Application Deployment (Kubernetes)

We need to deploy a **guestbook application** with Redis as the backend and a PHP frontend.

## Back-end Tier

1. **Redis Master Deployment**
    - Name: `redis-master`
    - Replicas: `1`
    - Container name: `master-redis-devops`
    - Image: `redis`
    - Resources: `cpu=100m`, `memory=100Mi`
    - Container port: `6379`
    - Service: `redis-master` on port `6379`

2. **Redis Slave Deployment**
    - Name: `redis-slave`
    - Replicas: `2`
    - Container name: `slave-redis-devops`
    - Image: `gcr.io/google_samples/gb-redisslave:v3`
    - Resources: `cpu=100m`, `memory=100Mi`
    - Env: `GET_HOSTS_FROM=dns`
    - Container port: `6379`
    - Service: `redis-slave` on port `6379`

## Front-end Tier

1. **Frontend Deployment**
    - Name: `frontend`
    - Replicas: `3`
    - Container name: `php-redis-devops`
    - Image: `gcr.io/google-samples/gb-frontend@sha256:a908df8486ff66f2c4daa0d3d8a2fa09846a1fc8efd65649c0109695c7c5cbff`
    - Resources: `cpu=100m`, `memory=100Mi`
    - Env: `GET_HOSTS_FROM=dns`
    - Container port: `80`

2. **Frontend Service**
    - Name: `frontend`
    - Type: `NodePort`
    - Port: `80`
    - NodePort: `30009`

---

✅ At the end, the **Guestbook app** should be accessible from the browser via the NodePort service.
