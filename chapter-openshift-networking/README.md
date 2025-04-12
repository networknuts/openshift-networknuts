# 🚀 OpenShift Assignment: Multi-Project App Deployment, Network Policies & Routing

In this assignment, you will work with OpenShift projects, deploy applications, configure advanced network policies, and explore different types of routes. Carefully read each section and complete the tasks as described.

---

## ✅ Task 1: Create Projects and Deploy Applications

Create the following OpenShift projects and deploy apps using the specified container image:

**Image for All Apps**:  
`docker.io/nginxinc/nginx-unprivileged:latest`

| Project      | App Name |
|--------------|----------|
| development  | app1     |
| testing      | app2     |
| quality      | app3     |
| quality      | app4     |
| production   | app5     |
| production   | app6     |

> Make sure all applications are running in their respective namespaces and are exposed via services.

---

## ✅ Task 2: Configure Network Policies in Production

In the `production` project, implement the following network policies:

1. **Deny all incoming traffic by default**
2. **Allow all traffic from the `development` namespace**
3. **Allow traffic from the `quality` namespace**, but **only from `app3`**, not `app4`
4. **Allow traffic from the `testing` namespace** to **`app6` only** and **only on port `8080`**

> Ensure that the network policies are properly scoped and tested for correctness using pod-to-pod communication checks.

---

## ✅ Task 3: Configure Routes for `app6`

1. Create two routes for the `app6` application in the `production` project:
   - **Insecure Route** (HTTP)
   - **Edge-Terminated Route** (HTTPS via TLS termination at the router)

2. Configure local DNS resolution for these routes by editing the `/etc/hosts` file on your system.

> Ensure both routes are accessible via curl or browser using the domain mapped in `/etc/hosts`.

---

## ✅ Task 4: Create a Passthrough Route Using Provided Repo

1. Clone the following GitHub repository:
https://github.com/networknuts/openshift-content

2. Navigate to the appropriate folder containing:
- `app.config`
- `create-certs.sh`
- `https-app.yml`

3. Use the provided resources to:
- Generate the required TLS certificates using `create-certs.sh`
- Create a **passthrough** route for the application

4. Validate the route using curl or a browser with HTTPS enabled.

---

## 📎 Submission Checklist

- ✅ All 6 applications deployed in the correct namespaces
- ✅ Network policies applied and verified in the `production` namespace
- ✅ Both insecure and edge routes for `app6` tested with DNS
- ✅ Passthrough route created using provided content and tested

---

🎯 **Tips**:
- Use `oc get pods -A` and `oc get netpol -n production` to verify progress.
- For DNS testing, ensure your `/etc/hosts` entries resolve correctly.
- Validate network policies using temporary busybox or curl pods in source namespaces.

Happy Hacking! 💻  
*– Network Nuts DevOps Team*
