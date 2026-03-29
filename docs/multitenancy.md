# Multitenancy in Kubernetes

## Solutions

> Multi-tenancy is a Kubernetes cluster model or architecture model in which a single cluster’s resources are shared among multiple tenants.
Examples of the shared cluster resources include CPU, memory, networking, and control plane resources. ([ContainIQ](https://www.containiq.com/post/kubernetes-multi-tenancy))

### CAPN

> Cluster API Provider for Nested Clusters

→ [docs](https://github.com/kubernetes-sigs/cluster-api-provider-nested/blob/main/docs/README.md)

### Capsule (by Clastix)

> A multi-tenancy and policy-based framework for Kubernetes

→ [capsule.clastix.io](https://capsule.clastix.io/), [code](https://github.com/clastix/capsule), [docs](https://capsule.clastix.io/docs/general/)

See also:

* [clastix.io](https://clastix.io/kubernetes-multi-tenancy)

### Kamaji (by Clastix)

> Kamaji deploys and operates Kubernetes at scale with a fraction of the operational burden

→ [kamaji.clastix.io](https://kamaji.clastix.io/), [code](https://github.com/clastix/kamaji)

See also:

* [Operate Kubernetes at scale with Clastix Kamaji and SUSE Rancher](https://www.suse.com/c/operate-kubernetes-at-scale-with-clastix-kamaji-and-suse-rancher/) - November 11, 2022

### kcp (by Red Hat)

> Kubernetes-like control plane

→ [code](https://github.com/kcp-dev/kcp)

### kiosk (by Loft Labs)

> Multi-Tenancy Extension For Kubernetes - Secure Cluster Sharing & Self-Service Namespace Provisioning

→ [code](https://github.com/loft-sh/kiosk)

### KubePlus

> KubePlus is a turn-key solution to transform any containerized application into a SaaS

→ [code](https://github.com/cloud-ark/kubeplus)

### Kubeslice

> KubeSlice enables Kubernetes pods and services to communicate seamlessly across clusters, clouds, edges, and data centers by creating logical application boundaries known as Slices.
> It combines network, application, and deployment services in a framework to accelerate application deployment in a multi-cluster, multi-tenant environment.

→ [kubeslice.io](https://kubeslice.io/), [GitHub Org](https://github.com/kubeslice)

See also:

* [How KubeSlice implements Multi-tenancy](https://avesha.io/blogs/how-kubeslice-implements-multi-tenancy/) - July 24, 2022

### vcluster (by Loft Labs)

> Virtual Kubernetes Clusters that run inside regular namespaces

→ [vcluster.com](https://www.vcluster.com/), [code](https://github.com/loft-sh/vcluster), [docs](https://www.vcluster.com/docs/what-are-virtual-clusters)

### VirtualCLuster

> VirtualCluster represents a new architecture to address various Kubernetes control plane isolation challenges. It extends existing namespace based Kubernetes multi-tenancy model by providing each tenant a cluster view.
> VirtualCluster completely leverages Kubernetes extendability and preserves full API compatibility. That being said, the core Kubernetes components are not modified in virtual cluster.

→ [code](https://github.com/kubernetes-sigs/cluster-api-provider-nested/tree/main/virtualcluster)

## References

* [Kubernetes Documentation / Concepts / Security / Multi-tenancy](https://kubernetes.io/docs/concepts/security/multi-tenancy/)
* [Multi-tenancy in Kubernetes: implementation and optimization](https://www.cncf.io/blog/2022/11/09/multi-tenancy-in-kubernetes-implementation-and-optimization/) by Feng Ye - November 9, 2022
* [Clusters for all!](https://blog.joshgav.com/posts/cluster-level-multitenancy) by Josh Gavant - May 16, 2022
