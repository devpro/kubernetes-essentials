# Kubernetes related projects

## Cloud Native Application Bundle (CNAB)

> A spec for packaging distributed apps. CNABs facilitate the bundling, installing and managing of container-native apps — and their coupled services.

Reference: [cnab.io](https://cnab.io/)

## Cloud Native Buildpacks

> Cloud Native Buildpacks transform your application source code to images that can run on any cloud.

Reference: [buildpacks.io](https://buildpacks.io/)

## Container Network Interface (CNI)

> CNI (Container Network Interface), a Cloud Native Computing Foundation project, consists of a specification and libraries for writing plugins to configure network interfaces in Linux containers, along with a number of supported plugins.
> CNI concerns itself only with network connectivity of containers and removing allocated resources when the container is deleted.

Reference: [containernetworking/cni](https://github.com/containernetworking/cni)

<details>
  <summary>Read more</summary>

- [containernetworking/plugins](https://github.com/containernetworking/plugins)
- `kubeadmin` uses CNI as the default network interface mechanism since v1.6.0.
- [CNCF Blog - CNCF Hosts Container Networking Interface (CNI)](https://www.cncf.io/blog/2017/05/23/cncf-hosts-container-networking-interface-cni/) - May-23 '17
- [SlideShare - Introduction to the Container Network Interface (CNI)](https://www.slideshare.net/weaveworks/introduction-to-the-container-network-interface-cni) - Sep-01 '17
- Sample of configuration file:
  
  ```json
  {
    "cniVersion": "0.2.0",
    "name": "mynet",
    "type": "bridge",
    "bridge": "cni0",
    "isGateway": true,
    "ipMasq": true,
    "ipam": {
      "type": "host-local",
      "subnet": "10.22.0.0/16",
      "routes": [
        { "dst": "0.0.0.0/0" }
      ]
    }
  }
  ```
  
</details>

## Container Runtime Interface (CRI)

- [Introducing Container Runtime Interface (CRI) in Kubernetes](https://kubernetes.io/blog/2016/12/container-runtime-interface-cri-in-kubernetes/) - December 19, 2016
- [kubernetes-sigs/cri-tools](https://github.com/kubernetes-sigs/cri-tools)

## containerd

> An industry-standard container runtime with an emphasis on simplicity, robustness and portability

Reference: [containerd.io](https://containerd.io/), [containerd/containerd](https://github.com/containerd/containerd)

## CoreDNS

> CoreDNS is a DNS Server

Reference: [coredns.io](https://coredns.io/), [coredns/coredns](https://github.com/coredns/coredns)

See also: [Helm chart](https://hub.helm.sh/charts/stable/coredns)

## cri-o

> Lightweight Container Runtime for Kubernetes

Reference: [cri-o.io](https://cri-o.io/)

## dapr (Distributed Application Runtime)

> An event-driven, portable runtime for building microservices on cloud and edge.

Reference: [dapr.io](https://dapr.io/), [dapr/dapr](https://github.com/dapr/dapr), [Announcement](https://cloudblogs.microsoft.com/opensource/2019/10/16/announcing-dapr-open-source-project-build-microservice-applications/)

## Knative

> Kubernetes-based platform to deploy and manage modern serverless workloads.

Reference: [knative.dev](https://knative.dev/), [GitHub](https://github.com/knative)

## kpack

Kubernetes Native Container Build Service provided by Pivotal

Reference: [pivotal/kpack](https://github.com/pivotal/kpack)

See also: [TGI Kubernetes 091: kpack](https://www.youtube.com/watch?v=4zkRX9PSJ5k&feature=youtu.be)

## Kubebuilder

> Kubebuilder is a framework for building Kubernetes APIs using custom resource definitions (CRDs).

Reference: [book.kubebuilder.io](https://book.kubebuilder.io/introduction.html), [kubernetes-sigs/kubebuilder](https://github.com/kubernetes-sigs/kubebuilder)

## OCI (Open Container Initiative)

> The Open Container Initiative is an open governance structure for the express purpose of creating open industry standards around container formats and runtimes.

Reference: [opencontainers.org](https://opencontainers.org/), [opencontainers/runtime-spec](https://github.com/opencontainers/runtime-spec)

## runc

> runc is a CLI tool for spawning and running containers according to the OCI specification.

Reference: [opencontainers/runc](https://github.com/opencontainers/runc)
