# Kubernetes ClusterRole object

[Kubernetes Documentation/Reference/API Access Control/Using RBAC Authorization](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)

> ClusterRole is a non-namespaced resource. The resources have different names (Role and ClusterRole) because a Kubernetes object always has to be either namespaced or not namespaced; it can't be both.
>
> ClusterRoles have several uses. You can use a ClusterRole to define permissions on:
>
> - namespaced resources and be granted within individual namespace(s)
> - namespaced resources and be granted across all namespaces
> - define permissions on cluster-scoped resources

## Command line examples

```bash
# count the number of clusterroles in the cluster
k get clusterrole | wc -l

# view API discovery roles
kubectl get clusterroles system:discovery -o yaml

k create clusterrole node-admin --verb=list --resource=nodes

kubectl api-resources

# it will automatically add the correct apigroups
k create clusterrole storage-admin --verb=list --resource=persistentvolumes,storageclasses
```

## Manifest examples

- A ClusterRole that can be used to grant read access to secrets in any particular namespace, or across all namespaces (depending on how it is bound):

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  # "namespace" omitted since ClusterRoles are not namespaced
  name: secret-reader
rules:
  - apiGroups: [""]
    # at the HTTP level, the name of the resource for accessing Secret objects is "secrets"
    resources: ["secrets"]
    verbs: ["get", "watch", "list"]
```
