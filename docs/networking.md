# Networking in Kubernetes

- [The Kubernetes Networking Guide](https://www.tkng.io/)

## CNI Providers

- [Kubernetes Network Plugins](https://kubernetes.io/docs/concepts/extend-kubernetes/compute-storage-net/network-plugins/)
- [Comparing Kubernetes CNI providers](https://kubevious.io/blog/post/comparing-kubernetes-container-network-interface-cni-providers) by Kubevious (2021)

## Linux basics

```bash
ip link

ip link add v-net-0 type bridge

ip link set dev v-net-0 up

ip link add veth-red type veth peer name veth-red-br

ip link set veth-red netns red

ip -n red addr add 192.168.15.1 dev veth-red

ip -n red link set veth-red up

ip netns exec blue ip route add 192.168.1.0/24 via 192.168.15.5

ip addr

ip addr add 192.168.1.10/24 dev eth0

ip route

ip route add 192.168.1.0/24 via 192.168.2.1

cat /proc/sys/net/ipv4/ip_forward

arp

netstat -plnt

route

iptables -t nat -A POSTROUTING -s 192.168.15.0/24 -j MASQUERADE
```

## Recipes

- Get the network interface configured for cluster connectivity on the master node

```bash
ip link
```

- Get the IP address assigned to the master node on this interface

```bash
kubectl get nodes -o wide
```

- Get the route used to ping google from the master node (what is the IP address of the Default Gateway?)

```bash
ip route show default
```

- Get the port the kube-scheduler is listening on in the master node

```bash
netstat -nplt
```

- Get CNI configuration

```bash
ps -aux | grep kubelet
```

- Get the CNI plugin configured to be used on this kubernetes cluster

```bash
ls /etc/cni/net.d/
```

- What is the POD IP address range configured by weave?

```bash
ip addr show weave
```

- What is the default gateway configured on the PODs scheduled on node03? (Try scheduling a pod on node03 and check ip route output)

```bash
# create pod with nodeName set and wait for it to be in running state, get its ip

# look at the route and the gateway
ip route get 10.32.0.3

# or ssh in the pod and execute
ip route
```

- What network range are the nodes in the cluster part of?

```bash
# look at ens3 interface
ip addr
```

- What is the range of IP addresses configured for PODs on this cluster?

```bash
# look at starting log message with ipalloc-rande
kubectl logs <weave-pod-name> weave -n kube-system
```

- What is the IP Range configured for the services within the cluster?

```bash
# look at kube api server configuration
cat /etc/kubernetes/manifests/kube-apiserver.yaml | grep cluster-ip-range
```

- What type of proxy is the kube-proxy configured to use?

```bash
k logs kube-proxy-lx9pq -n kube-system
```

## General ideas

Any K8s compliant CNI can be leveraged with RKE/k3s: bring your own CNI!

## Documentation

- [Container Network Interface (CNI) Providers](https://ranchermanager.docs.rancher.com/faq/container-network-interface-providers)
- [Troubleshooting](https://ranchermanager.docs.rancher.com/troubleshooting/other-troubleshooting-tips/networking)
- [Rancher Nodes Ports](https://ranchermanager.docs.rancher.com/getting-started/installation-and-upgrade/installation-requirements/port-requirements)
- Knowledge base
  - [Will Rancher fix the issue and release a patch, if the problem is root-caused in one of the Rancher 2.x CNI plugin add-ons such as Weave, Cisco ACI, Cilium, and Calico?](https://www.suse.com/support/kb/doc/?id=000020468)

## Cisco ACI (Application Centric Infrastructure)

- [Cisco ACI for Data Center](https://www.cisco.com/c/en/us/solutions/data-center-virtualization/application-centric-infrastructure/index.html)
- [Cisco ACI and Rancher Integration](https://www.cisco.com/c/en/us/td/docs/dcn/aci/containers/cisco-aci-and-rancher-integration.html)
- [RKE Cluster Configuration Reference > Project Network Isolation](https://rancher.com/docs/rancher/v2.6/en/cluster-admin/editing-clusters/rke-config-reference/#project-network-isolation)
- [ACI Virtualization Compatibility Matrix](https://www.cisco.com/c/dam/en/us/td/docs/Website/datacenter/aci/virtualization/matrix/virtmatrix.html)

## VMware NSX-T

### NSX-T overview

- [VMware NSX Documentation](https://docs.vmware.com/en/VMware-NSX/index.html)
  - [Key Concepts](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/3.2/installation/GUID-A1BBC650-CCE3-4AC3-A774-92B195183492.html)
  - [NSX-T Architecture Technical Overview](https://nsx.techzone.vmware.com/resource/vmware-nsx-t-architecture-technical-overview)
  - [NSX-T Reference Design Guide](https://nsx.techzone.vmware.com/resource/nsx-t-reference-design-guide-3-0) ([PDF](https://communities.vmware.com/t5/VMware-NSX-Documents/VMware-NSX-T-Reference-Design/ta-p/2778093))
  - [NSX-T Architecture and Components](https://nsx.techzone.vmware.com/sites/default/files/imported-images/node_2501/NSX-T-Reference-Design-Guide-3-0/NSX-T-Reference-Design-Guide-3-0.007.png)
- [Understand NSX-T learning path](https://nsx.techzone.vmware.com/understand-nsx-t)
- [VMware NSX Training and Demos](https://www.youtube.com/playlist?list=PLdYldEmmLm2nBcfxkp-wzE4SCohw2ynD3)
- [NSX-T, Kubernetes and Microsegmentation](https://www.virtualthoughts.co.uk/2018/08/01/nsx-t-kubernetes-and-microsegmentation/) - August 1, 2018

### NSX Container Plug-in (NCP)

- [Overview of NSX Container Plug-in](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/3.2/ncp-kubernetes/GUID-52A92986-0FDF-43A5-A7BB-C037889F7559.html)
  - [Installation Overview](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/3.2/ncp-kubernetes/GUID-22D54FC5-4B06-4FE1-86A9-96A953FA15B9.html)
  - [Ingress](https://docs.vmware.com/en/VMware-NSX-T-Data-Center/3.2/ncp-kubernetes/GUID-E03D6EE5-9C6C-457F-AD81-25CF2056F4D8.html)
- [Solve Container Networking Challenges with NSX Container Plugin](https://blogs.vmware.com/networkvirtualization/2020/05/nsx-container-plugin.html/) - May 7, 2020
- [NSX-T NSX Container Plugin NCP Architecture - Support Kubernetes](https://www.youtube.com/watch?v=DPlr7K2eEow)
- [Kubernetes and NSX-T – Part 1 Deploying Container Hosts](https://vnuggets.com/2019/10/02/kubernetes-and-nsx-t-part1-deploying-container-hosts/) - October 2, 2019
- [Using the NSX-T CNI with RKE2](https://www.virtualthoughts.co.uk/2022/07/04/using-the-nsx-t-cni-with-rke2/) ([GitHub](https://github.com/David-VTUK/rke2-nsxt)) - July 4, 2022
  - [RKE2 and NSX-T with Terraform](https://github.com/David-VTUK/rke2-nsxt-terraform)
- [VMware NSX-T 2.5.x and Kubernetes (K8S) Guide](https://github.com/dumlutimuralp/k8s-with-nsx-t-2.5.x)

### Antrea

> Antrea is a Kubernetes-native project that implements the Container Network Interface (CNI) and Kubernetes NetworkPolicy thereby providing network connectivity and security for pod workloads.
Antrea extends the benefit of programmable networks from Open vSwitch (OVS) to Kubernetes.

→ [antrea.io](https://antrea.io/), [GitHub](https://github.com/antrea-io/antrea)

- [Connect and Secure your Apps with Antrea and VMware NSX-T 3.2](https://blogs.vmware.com/networkvirtualization/2022/02/connect-and-secure-your-apps-with-antrea-and-vmware-nsx-t-3-2.html/) - February 16, 2022
