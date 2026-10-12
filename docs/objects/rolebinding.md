# Kubernetes RoleBinding object

[Kubernetes Documentation/Reference/API Access Control/Using RBAC Authorization](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)

> A role binding grants the permissions defined in a role to a user or set of users. It holds a list of subjects (users, groups, or service accounts), and a reference to the role being granted. A RoleBinding grants permissions within a specific namespace whereas a ClusterRoleBinding grants that access cluster-wide.
>
> A RoleBinding may reference any Role in the same namespace. Alternatively, a RoleBinding can reference a ClusterRole and bind that ClusterRole to the namespace of the RoleBinding. If you want to bind a ClusterRole to all the namespaces in your cluster, you use a ClusterRoleBinding.

## Command line examples

```bash
# get user or group using the role
k describe rolebinding <role-name>

kubectl create rolebinding dev-user-operator-binding --role=operator --user=dev-user --namespace=blue
```

## Manifest examples

- This role binding allows "jane" to read pods in the "default" namespace. You need to already have a Role named "pod-reader" in that namespace.

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: default
subjects:
  # You can specify more than one "subject"
  - kind: User
    name: jane # "name" is case sensitive
    apiGroup: rbac.authorization.k8s.io
roleRef:
  # "roleRef" specifies the binding to a Role / ClusterRole
  kind: Role # this must be Role or ClusterRole
  name: pod-reader # this must match the name of the Role or ClusterRole you wish to bind to
  apiGroup: rbac.authorization.k8s.io
```
  