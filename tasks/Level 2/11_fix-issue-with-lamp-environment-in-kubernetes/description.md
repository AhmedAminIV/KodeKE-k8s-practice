# 📝 Issue Description

The WordPress website running on a **LAMP stack** in the Kubernetes cluster\
(deployment: `lamp-wp`, service: `lamp-service`) has gone down.

From the application logs, the problem was identified as **database connectivity issues**.
The WordPress container requires environment variables for MySQL connection, 
but they were missing or misconfigured.

The required environment variables are:

- `MYSQL_ROOT_PASSWORD`
- `MYSQL_DATABASE`
- `MYSQL_USER`
- `MYSQL_PASSWORD`
- `MYSQL_HOST`

Without these variables, the WordPress pod cannot establish a connection to the database,
which caused the downtime.

✅ **Fix:** Update the deployment `lamp-wp` to include the correct environment variables\
so that the WordPress application can connect to the database successfully.
