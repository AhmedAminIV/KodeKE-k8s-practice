# Redis Deployment on Kubernetes

The Nautilus application development team identified performance issues in one of their applications
and decided to introduce an in-memory caching utility.
As a first step, they want to deploy **Redis** on the Kubernetes cluster for testing.

### Requirements:
1. Create a **ConfigMap** named `my-redis-config` with the following key-value pair:
    - `maxmemory 2mb` in `redis-config`.

2. Create a **Deployment** with the following specs:
    - **Name**: `redis-deployment`
    - **Replicas**: 1
    - **Image**: `redis:alpine`
    - **Container name**: `redis-container`
    - **Resource request**: `1 CPU`
    - **Port**: `6379`

3. Configure volumes:
    - An **emptyDir** volume named `data` mounted at `/redis-master-data`
    - A **ConfigMap** volume named `redis-config` mounted at `/redis-master`

4. Ensure the deployment is **up and running**.
