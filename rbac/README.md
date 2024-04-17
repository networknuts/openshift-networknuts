
# Openshift Role Based Access Control

This documentation is based on the Openshift Series by Network Nuts

## 1. Creating Groups

We need to create a group named devops and a group named auditors

```bash
  oc adm groups new devops
  oc adm groups new auditors
```

## 2. Adding Users into Groups

Add the aryan user into the devops group and the jane and john users into the auditors group

```bash
  oc adm groups add-users devops aryan
  oc adm groups add-users auditors john jane
  oc get groups 
```

## 3. Assign Permissions onto Groups
Assign the cluster admin privileges to the devops group and the view privileges to the auditors group 

```bash
  oc adm policy add-cluster-role-to-group cluster-admin devops
  oc adm policy add-cluster-role-to-group view auditors 
```
