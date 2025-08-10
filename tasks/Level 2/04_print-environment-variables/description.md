## 📄 Task Description

The Nautilus DevOps team is setting up pre-requisites for an application\
that will send greetings to different users.  
A sample deployment needs to be tested with the following configuration:

**Requirements:**

1. **Pod**
    - Name: `print-envars-greeting`
    - Container name: `print-env-container`
    - Image: `bash`
2. **Environment Variables**
    - `GREETING` = `Welcome to`
    - `COMPANY` = `DevOps`
    - `GROUP` = `Ltd`
3. **Command**
    - `["/bin/sh", "-c", 'echo "$(GREETING) $(COMPANY) $(GROUP)"']`
4. **Restart Policy**
    - `Never` (to avoid crash loop back)

**Verification:**
- Check the output with:
  ```bash
  kubectl logs -f print-envars-greeting
