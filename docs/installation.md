# Installation

## Quick start

Several options to start with a new Kubernetes cluster:

- Managed Kubernetes services (by Cloud Provider):
  - [Amazon Elastic Kubernetes Service (EKS)](https://aws.amazon.com/eks/)
  - [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/en-us/products/kubernetes-service/)
  - [Google Kubernetes Engine (GKE)](https://cloud.google.com/kubernetes-engine/)
- Kubernetes management tools:
  - [Broadcom VMware Tanzu Kubernetes Grid](https://tanzu.vmware.com/kubernetes-grid) (replaced Pivotal Container Service, aka PKS, with the acquisition of Pivotal of VMware)
  - [IBM Red Hat OpenShift](https://www.openshift.com/)
  - [SUSE Rancher](https://www.rancher.com/)
- [Kubernetes distributions](distributions)
- Kubernetes installation tools for Production-grade clusters:
  - kubeadm
  - kops
  - kubespray
- Test clusters
  - [Kind (Kubernetes in Docker)](https://kind.sigs.k8s.io/) ([kubernetes-sigs/kind](https://github.com/kubernetes-sigs/kind)): fast and easy testing of clusters
    - [Kubernetes Podcast #69 kind, with Ben Elder (September 3, 2019)](https://kubernetespodcast.com/episode/069-kind/)
    - [everyday-cheatsheets/kind](https://github.com/devpro/everyday-cheatsheets/blob/main/docs/cncf/kind.md)
  - [Minikube](https://github.com/devpro/everyday-cheatsheets/blob/master/docs/minikube.md) on all machines
  - [MicroK8s](https://microk8s.io/docs) from Canonical on Ubuntu
- Kubernetes on workstations
  - [Docker Desktop](https://www.docker.com/products/kubernetes) on Windows and MacOS
  - Rancher Desktop
  - Podman Desktop

## Cluster creation

### General thought

- [Picking the Right Solution](https://pwittrock.github.io/docs/setup/pick-right-solution/)
- [Kubernetes The Hard Way by Kelsey Hightower](https://github.com/kelseyhightower/kubernetes-the-hard-way)

### Deployment configurations

- Single-node
- Single head node, multiple workers
- Multiple head nodes with HA, multiple workers
- HA etcd, HA head nodes, multiple workers

### Network

Networking is a central part of Kubernetes, but it can be challenging to understand exactly how it is expected to work. There are 4 distinct networking problems to address:

- Highly-coupled container-to-container communications
- Pod-to-Pod communications
- Pod-to-Service communications
- External-to-Service communications

Reference: [Documentation > Concepts > Cluster Administration > Cluster Networking](https://kubernetes.io/docs/concepts/cluster-administration/networking/)

A network must be defined to manage the cluster and avoid any IP conflict. Available plugins may implement [Container Network Interface (CNI)](https://github.com/devpro/kubernetes-certification-2020/blob/master/docs/projects.md#container-network-interface-cni), a CNCF project.

#### Network plugins (pod networking)

Reference:

- [Documentation > Concepts > Extending Kubernetes > Compute, Storage, and Networking Extensions > Network Plugins](https://kubernetes.io/docs/concepts/extend-kubernetes/compute-storage-net/network-plugins/)
- [Documentation > Concepts > Cluster Administration > Installing Addons](https://kubernetes.io/docs/concepts/cluster-administration/addons/)
- [Virtual Extensible LAN (VXLAN)](https://en.wikipedia.org/wiki/Virtual_Extensible_LAN)

| Name                                                                      | Network Model | Allow vxlan | Allow network policies | Can encrypt all TCP and UDP traffic |
| ------------------------------------------------------------------------- | ------------- | ----------- | ---------------------- | ----------------------------------- |
| [`Calico`](https://www.projectcalico.org/)                                | Level 3       | Yes         | Yes                    | Yes                                 |
| [`Weave Net`](https://www.weave.works/oss/net/)                           | Level 2       | Yes         |                        | Yes                                 |
| [`Flannel`](https://github.com/coreos/flannel)                            | Level 2       | Yes         |                        |                                     |
| [`Kube Router`](https://www.kube-router.io/)                              | Level 3       |             | Yes                    |                                     |
| [`Romana`](https://romana.io/) ([code](https://github.com/romana/romana)) | Level 3       |             | Yes                    |                                     |
| [`Kopeio`](https://github.com/kopeio/networking)                          | Level 2       | Yes         |                        | Yes                                 |

### Tools

3 choices:

- [kubeadm](./tools/kubeadm.md): boostrap quickly a cluster (appeared in v1.4, stabe & HA with V1.15)
- [kops](https://kubernetes.io/docs/setup/production-environment/tools/kops/)
- [kubespray](https://kubernetes.io/docs/setup/production-environment/tools/kubespray/)

### Addons

#### Metrics

- [Kubernetes Documentation > Tasks > Monitoring, Logging, and Debugging > Resource metrics pipeline](https://kubernetes.io/docs/tasks/debug-application-cluster/resource-metrics-pipeline/)
- [Kubernetes Documentation > Tasks > Configure Pods and Containers > Assign CPU Resources to Containers and Pods](https://kubernetes.io/docs/tasks/configure-pod-container/assign-cpu-resource/)
- [kubernetes-sigs/metrics-server](https://github.com/kubernetes-sigs/metrics-server)

### Configuration management systems

See recipes with Ansible, Chef, Puppet, Terraform.

### Hyperkube

As of July of 2020, Kyperkube seems deprecated. The image build has been removed from Kubernetes base images, see [PR#88676](https://github.com/kubernetes/kubernetes/pull/88676).
