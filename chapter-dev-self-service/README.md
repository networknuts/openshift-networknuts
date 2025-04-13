# 📦 OpenShift Assignment: Resource Quotas, Limit Ranges & Cluster-Wide Policies

This assignment covers advanced resource management in OpenShift using ResourceQuotas, LimitRanges, and ClusterResourceQuotas. You will also learn how to modify project templates to enforce default policies automatically.

---

## ✅ Task 1: Create a Namespace-Level ResourceQuota

Create a `ResourceQuota` YAML that restricts the following in a single namespace:

- **Memory Limit**: `1Gi`
- **CPU Limit**: `1 CPU`
- **Pod Count**: Maximum `10` pods
- **Secrets**: Maximum `12`
- **Services**: Maximum `5`

> Apply this quota to a namespace of your choice and verify enforcement using `oc describe quota`.

---

## ✅ Task 2: Create a Container-Level LimitRange

Define a `LimitRange` that applies resource constraints at the container level with the following rules:

- **Minimum resources per container**:  
  - CPU: `100m`  
  - Memory: `100Mi`

- **Maximum resources per container**:  
  - CPU: `2 CPU`  
  - Memory: `1Gi`

- **Default resources when not defined by the user**:  
  - CPU: `200m` (min) to `500m` (max)  
  - Memory: `256Mi` (min) to `512Mi` (max)

> Apply this to a namespace and test by deploying a pod with no defined resources.

---

## ✅ Task 3: Create a ClusterResourceQuota

Define a `ClusterResourceQuota` that applies the same limits as Task 1, but across **multiple namespaces** that are labeled with `sdlc=devops`.

| Resource | Limit         |
|----------|---------------|
| Memory   | `1Gi`         |
| CPU      | `1 CPU`       |
| Pods     | `10`          |
| Secrets  | `12`          |
| Services | `5`           |

> Make sure to label multiple namespaces with `sdlc=devops` and confirm that the cluster-wide quota applies to all of them.

---

## ✅ Task 4: Modify Project Bootstrap Template

Update the **default OpenShift project template** so that every new project automatically includes the `LimitRange` defined in Task 2.


## Submission Checklist
✅ ResourceQuota YAML created and applied

✅ LimitRange YAML created and tested

✅ ClusterResourceQuota created and applied to multiple labeled namespaces

✅ Project template modified and tested for automatic limit range application

💡 Pro Tip: Use oc get limitrange, oc describe quota, and oc get clusterresourcequota to verify your resources.

Happy Automating! ⚙️
– Network Nuts DevOps Team
