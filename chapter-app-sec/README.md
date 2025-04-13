# 🔐 OpenShift Assignment: App Security, Image Cleanup & Cluster Logging

This assignment is focused on securing container deployments, automating cluster image maintenance, and collecting logs for troubleshooting and auditing. Follow each task step-by-step and verify your results.

---

## ✅ Task 1: Deploy NGINX with Proper SCC in a Secure Namespace

1. **Create a New Project**
   - Project name: `app-sec`

2. **Deploy NGINX**
   - Image: `docker.io/library/nginx:latest`
   - Attempt to deploy this image as-is.

3. **Troubleshoot the Failure**
   - The default deployment will **fail due to security context constraints (SCC)**.
   - Investigate using `oc describe pod`, `oc logs`, and `oc adm policy who-can`.

4. **Fix the Issue**
   - Create and assign a **custom service account** with a suitable SCC that allows the container to run (e.g., `anyuid` or `nonroot` depending on the image).
   - Update the deployment to use this service account.

> ✅ Final Outcome: NGINX should run successfully in the `app-sec` namespace using a secure, controlled configuration.

---

## ✅ Task 2: Automate Deletion of Old Container Images

1. **Research & Identify Cleanup Process**
   - Understand how OpenShift Garbage Collection and Image Pruner works.
   - Focus on deleting **container images older than 90 days** from the internal registry.

2. **Create a Kubernetes CronJob**
   - Schedule: **Every Sunday at 12:00 AM**
   - Task: Run image pruning command targeting images older than 90 days
   - Retain logs of:
     - **Last 10 successful runs**
     - **Last 10 failed runs**

> ✅ Final Outcome: Automatic and auditable cleanup of stale container images every week.

---

## ✅ Task 3: Cluster Log Collection & Archiving

1. **Collect Cluster Logs**
   - Gather logs from core OpenShift components such as:
     - `kube-apiserver`
     - `kube-controller-manager`
     - `openshift-apiserver`
     - `etcd`, etc.

2. **Archive Logs with Cluster Info**
   - Create a `tar.gz` archive file using the format:  
     ```
     cluster-logs-<CLUSTER_ID>-<TIMESTAMP>.tar.gz
     ```
   - Use the current cluster ID and timestamp when naming the archive.

> ✅ Final Outcome: A single compressed tarball that includes all relevant logs with identifying metadata.

---

## 📎 Submission Checklist

- [ ] NGINX successfully deployed in `app-sec` using proper SCC and service account
- [ ] CronJob YAML created and tested for weekly image cleanup
- [ ] Log archive named with cluster ID and timestamp available for submission

---

💡 **Pro Tip**:
- Use `oc get events` and `oc get pods -o yaml` to debug deployment issues.
- Use `oc adm prune images --keep-younger-than=90d` for image cleanup tasks.
- Use `oc adm must-gather` or `oc adm inspect` for log collection.

Stay Secure, Stay Clean! 🛡️  
*– Network Nuts DevOps Team*
