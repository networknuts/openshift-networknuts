# 🚀 OpenShift Hands-On Assignment  
**Topics Covered**: YAML Generation · Templates · Helm Charts · Kustomize

Welcome to your next OpenShift assignment. In this task, you'll work with different application deployment strategies on OpenShift, including YAML generation, template-based deployments, Helm charts, and Kustomize.

Complete all tasks below and prepare your screenshots or YAMLs for submission.

---

## ✅ Task 1: Create a YAML Using `oc new-app` Dry Run

Use the `oc new-app` command with the dry-run feature to generate a YAML manifest for deployment.

- **Application Name**: `nginx`
- **Container Image**: `docker.io/nginxinc/nginx-unprivileged:latest`
- **Requirement**: Save the generated YAML into a file named `nginx.yaml`.

---

## ✅ Task 2: Deploy PostgreSQL Using OpenShift Template

Deploy a PostgreSQL application using OpenShift’s built-in template mechanism.

- **PostgreSQL Username**: `john`
- **PostgreSQL Password**: `networknuts`

Ensure the database pod is deployed and running successfully.

---

## ✅ Task 3: Deploy Etherpad Using Helm

Use the Helm chart from the following repository:

https://redhat-cop.github.io/helm-charts

- Deploy the **latest version** of the **Etherpad** application using this Helm chart.
- Verify that the application is running and accessible.

---

## ✅ Task 4: Deploy App Using Kustomize

1. **Clone the Repository**  
   Clone the following GitHub repository:
      https://github.com/networknuts/kustomize
2. **Understand the Structure**  
Explore the folder structure to understand how base and environment-specific overlays (`dev`, `prod`, etc.) are defined using Kustomize.

3. **Deploy All Environments**  
Deploy the application for each environment (`dev`, `prod`, etc.) defined in the repo.

---

## 📎 Submission Instructions

Submit the following as proof of completion:

- The `nginx.yaml` file generated in Task 1.
- Screenshots or short video recordings of:
- PostgreSQL deployment from Task 2.
- Etherpad running from Helm deployment in Task 3.
- Kustomize app deployment in Task 4 for each environment.

---

Happy Deploying! 🚀  
*– Network Nuts DevOps Team*
