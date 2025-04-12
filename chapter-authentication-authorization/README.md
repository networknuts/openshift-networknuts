# 🎓 OpenShift RBAC Assignment

Welcome to your OpenShift training task. This hands-on exercise will help you understand the role-based access control (RBAC) model in OpenShift by managing users, groups, permissions, and projects.

Please complete all tasks as described below.

---

## ✅ Task 1: Create Users

Using the `htpasswd` method, create the following users with the specified passwords:

| Username   | Password     |
|------------|--------------|
| john       | networknuts  |
| jane       | openshift    |
| developer  | developer    |
| arthur     | blinder      |
| thomas     | blinder      |

---

## ✅ Task 2: Create Groups

Create the following groups in your OpenShift cluster:

- `auditors`
- `developers`

---

## ✅ Task 3: Assign Users to Groups

Assign the users to the appropriate groups:

- Add `arthur` and `thomas` to the `auditors` group.
- Add `john`, `jane`, and `developer` to the `developers` group.

---

## ✅ Task 4: Remove Self-Provisioning Rights

Remove the default `self-provisioner` permission from the `system:authenticated:oauth` group to prevent regular users from creating their own projects.

---

## ✅ Task 5: Create Projects

Create the following two projects in your OpenShift cluster:

- `remus`
- `romulus`

---

## ✅ Task 6: Assign Group Permissions

Grant the following role-based access:

- Give the `auditors` group **read-only access** to the `remus` project.
- Give the `developers` group **edit access** to the `romulus` project.

---

## ✅ Task 7: Grant Cluster Admin Rights

Make the user `john` a **cluster-admin** in the OpenShift cluster.

---

## 📌 Submission Instructions

- Verify your setup is working by logging in as each user and checking their permissions.
- Submit a screenshot or short video of your completed work showing:
  - User creation
  - Group membership
  - Project listing
  - Role bindings

---

Happy Learning! 🚀  
*– Network Nuts DevOps Team*
