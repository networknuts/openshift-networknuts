# OpenShift Cluster Updates

This document covers the different aspects of updating an OpenShift Container Platform (OCP) cluster, including update channels, GUI and CLI update processes, Kubernetes version compatibility, API deprecation, and a comprehensive update checklist.

---

## 1. Update Channels

OpenShift provides several update channels to control the frequency and stability of available upgrades:

* **Stable**: Well-tested updates; recommended for production.
* **Fast**: Early access to minor updates; good for staging and testing.
* **Candidate**: Preview of upcoming stable releases; use for validation before promoting to Stable.
* **Nightly**: Daily builds; for development only.

You can view and change the channel with the CLI:

```bash
# Show current channel
oc get clusterversion version -o jsonpath='{.spec.channel}'

# Switch to a different channel
oc patch clusterversion version --type=merge -p '{"spec":{"channel":"<new-channel>"}}'
```

---

## 2. GUI Update Process

1. Log in to the OpenShift Web Console as a cluster administrator.
2. Navigate to **Home > Cluster Settings > Updates**.
3. The console will display the **Current version** and **Available updates** based on your channel.
4. Click **Check for Updates** to refresh available versions.
5. Select the desired update and click **Update Cluster**.
6. Review and confirm the update details.
7. Monitor progress under **Cluster Operators** for all to return to `Available` state.

---

## 3. CLI Update Process

1. **Check cluster version**:

   ```bash
   oc get clusterversion
   ```
2. **List available updates**:

   ```bash
   oc adm upgrade
   ```
3. **Perform the upgrade**:

   * To automatically apply the latest in your channel:

     ```bash
     oc adm upgrade --to-latest
     ```
   * To upgrade to a specific version:

     ```bash
     oc adm upgrade --to=<version>
     ```
4. **Verify upgrade progress**:

   ```bash
   oc get clusterversion
   oc get co   # ensure all ClusterOperators report AVAILABLE=True
   ```

---

## 4. OCP and Kubernetes Version Compatibility

| OCP Version | Kubernetes Version |
| :---------: | :----------------: |
|     4.7     |        1.20        |
|     4.8     |        1.21        |
|     4.9     |        1.22        |
|     4.10    |        1.23        |
|     4.11    |        1.24        |
|     4.12    |        1.25        |
|     4.13    |        1.26        |
|     4.14    |        1.27        |

> **Note:** Always refer to the [Red Hat documentation](https://docs.openshift.com) for the exact mapping for your cluster version.

---

## 5. API Deprecation

Kubernetes deprecates older API versions over time. When an API is deprecated:

* It moves from `v1beta1` → `v1`, and eventually is removed in a future release.
* Deprecated APIs emit warning messages when used.
* OpenShift maintains compatibility by backporting critical APIs longer, but you should migrate to supported APIs.

**How to identify deprecated APIs in your cluster**:

```bash
# List all API versions, highlighting deprecated ones
oc api-versions | grep -E "v1beta1|v1alpha1"

# Search for deprecated warnings in logs
oc logs -n openshift-apiserver $(oc get pods -n openshift-apiserver -o name) | grep -i deprecation
```

**Migration steps**:

1. Identify workloads using deprecated APIs (DeploymentConfigs, Apps/v1beta\* → Apps/v1).
2. Update YAML manifests to use the current API group/version.
3. Test on a non-production cluster.
4. Apply updated manifests in production.

---

## 6. Update Checklist

Use this checklist to ensure a smooth and reliable update:

1. **Pre-Update Planning**

   * Review OpenShift release notes for changes and deprecations.
   * Confirm support window and maintenance window.
   * Notify stakeholders of planned downtime (if any).

2. **Backup & Health Checks**

   * Take an etcd snapshot:

     ```bash
     oc adm etcd snapshot save latest-snapshot.db
     ```
   * Verify all cluster operators are healthy:

     ```bash
     oc get co
     ```
   * Ensure application backups and persistent volumes are intact.

3. **API Deprecation Audit**

   * Check for usage of deprecated Kubernetes APIs.
   * Update custom resources and manifests as needed.

4. **Channel Verification**

   * Confirm you are on the correct update channel for your environment.
   * Switch channels if preparing for a different release cadence.

5. **Dry Run (Optional)**

   * Test the upgrade in a staging/non-production cluster.
   * Validate application behavior post-upgrade.

6. **Perform the Upgrade**

   * GUI: Follow the steps in [Section 2](#2-gui-update-process).
   * CLI: Run commands from [Section 3](#3-cli-update-process).

7. **Post-Update Validation**

   * Confirm `oc get clusterversion` shows the new version.
   * Verify all ClusterOperators report `AVAILABLE=True`.
   * Check logs for errors or deprecation warnings.
   * Test critical application functionality.

8. **Cleanup & Documentation**

   * Archive the etcd snapshot if successful.
   * Update internal runbooks and change logs.
   * Communicate completion to stakeholders.

---

