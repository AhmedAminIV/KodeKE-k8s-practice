Got it 👍 here’s the **debugging steps in one clean Markdown block** so you can copy everything directly:
  
  ````markdown
  ### 🛠 Steps to Debug WordPress LAMP Stack Issue
  
  1. **Checked Service Ports**
Verified both NodePort and targetPort in `lamp-service`:
  ```bash
  kubectl get svc lamp-service -o wide
  ````
  
  2. **Checked Pod Logs**
Looked into logs of the WordPress pod to identify errors:
  
  ```bash
  kubectl logs <lamp-wp-pod>
  ```
  
  3. **Exec into the Pod**
Accessed the container to inspect and fix issues directly:
  
  ```bash
  kubectl exec -it <lamp-wp-pod> -- /bin/bash
  ```
  
  4. **Fixed Syntax Error**
  Corrected the syntax error in the configuration file inside the container.
  
  5. **Validated Fix**
  After changes, confirmed service connectivity and application access.
  