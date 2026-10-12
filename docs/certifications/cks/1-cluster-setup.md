# Kubernetes cluster setup

## Network Policies

> Use network security policies to restrict cluster level access  

✨ [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies),
[Declare Network Policy](https://kubernetes.io/docs/tasks/administer-cluster/declare-network-policy/)

⚡️ Notes:

* **NetworkPolicies** allow you to prevent or restrict network communication to and from Pods
* They are "an application-centric construct which allow you to specify how a pod is allowed to communicate with various network _entities_ over the network"
* They "do not conflict; they are additive"
* Ther are stateful, so the replies to outbound requests still reach the application

💡 Tips:

* Explain given YAML with online tools, like [Isovalent: Network Policy Editor](https://editor.networkpolicy.io/) or [Tufin: Kubernetes Network Policies Viewer](https://orca.tufin.io/netpol/)

⚗️ [Practice](practice/1.1-network-policies.md)

📝 Read more:

* [Anthos security blueprint: Restricting traffic](https://github.com/GoogleCloudPlatform/anthos-security-blueprints/tree/master/restricting-traffic)
* [Ahmet Alp Balkan: Kubernetes Network Policy Recipes](https://github.com/ahmetb/kubernetes-network-policy-recipes)
* [Calico: Get started with Kubernetes network policy](https://docs.projectcalico.org/security/kubernetes-network-policy)
* [Security People: An Introduction to Kubernetes Network Policies](https://reuvenharrison.medium.com/an-introduction-to-kubernetes-network-policies-for-security-people-ba92dd4c809d)

## CIS Benchmark

> Use CIS benchmark to review the security configuration of Kubernetes components (etcd, kubelet, kubedns, kubeapi)

⚡️ Notes:

* The [Center for Internet Security (CIS) Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes/) is the product of a community consensus process and consists of secure configuration guidelines developed for Kubernetes

🚀 [kube-bench](tools/kube-bench.md)

💡 Tips:

* Use `kube-bench` logs to view the CIS benchmark output
* The CIS benchmark output includes remediations steps one can follow to fix the issues that have been reported
* `kubeadm` clusters use a kubelet configuration file located at `/var/lib/kubelet/config.yaml` (can be seen from `/etc/systemd/system/kubelet.service.d/10-kubeadm.conf`)
* In a `kubeadm` cluster, control plane components run as static pods whose definitions are in `/etc/kubernetes/manifest` folder

⚗️ [Practice](practice/1.2-cis-benchmark.md)

📝 Read more:

* [Aqua: Kubernetes CIS Benchmark Best Practices](https://www.aquasec.com/cloud-native-academy/kubernetes-in-production/kubernetes-cis-benchmark-best-practices-in-brief/)
* [DevSec Hardening Framework: CIS Kubernetes Benchmark - InSpec Profile](https://github.com/dev-sec/cis-kubernetes-benchmark)
* [GKE: CIS Benchmarks](https://cloud.google.com/kubernetes-engine/docs/concepts/cis-benchmarks)
* [Microsoft Compliance: CIS Benchmarks](https://docs.microsoft.com/en-us/microsoft-365/compliance/offering-cis-benchmark)

## Ingress

> Properly set up Ingress objects with security control

✨ [Ingress > TLS](https://kubernetes.io/docs/concepts/services-networking/ingress/#tls),
[Generate Certificates Manually > openssl](https://kubernetes.io/docs/tasks/administer-cluster/certificates/#openssl)

💡 Tips:

* TLS termination can be implemented using an **Ingress**
* TLS certificates are stored as **Secret** which are referenced in the **Ingress** using the `spec.tls[].secretName`

⚗️ [Practice](practice/1.3-ingress.md)

📝 Read more:

* [Ingress Controllers](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/)
* [Set up Ingress on Minikube with the NGINX Ingress Controller](https://kubernetes.io/docs/tasks/access-application-cluster/ingress-minikube/)
* Ingress-Nginx Controller: [Installation Guide](https://kubernetes.github.io/ingress-nginx/deploy/), [TLS/HTTPS](https://kubernetes.github.io/ingress-nginx/user-guide/tls/)

## Node protection

> Protect node metadata and endpoints

✨ [Restricting cloud metadata API access](https://kubernetes.io/docs/tasks/administer-cluster/securing-a-cluster/#restricting-cloud-metadata-api-access),
[Kubelet authentication/authorization](https://kubernetes.io/docs/reference/access-authn-authz/kubelet-authn-authz/),
[Set Kubelet Parameters Via A Configuration File](https://kubernetes.io/docs/tasks/administer-cluster/kubelet-config-file/)

⚗️ [Practice](practice/1.4-node-protection.md)

📝 Read more:

* [Kubelet API, by Deep Network](https://www.deepnetwork.com/blog/2020/01/13/kubelet-api.html)
* [Setting up secure endpoints in Kubernetes](https://blog.cloud66.com/setting-up-secure-endpoints-in-kubernetes)
* [GKE Protecting cluster metadata](https://cloud.google.com/kubernetes-engine/docs/how-to/protecting-cluster-metadata)
* [Retrieving EC2 instance metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-data-retrieval.html)
* [EC2 Instance user data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html)

## GUI restriction

> Minimize use of, and access to, GUI elements

✨ [Deploy and Access the Kubernetes Dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)

📝 Read more:

* [Dashboard Access control](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/README.md)
* [Dashboard Creating sample user](https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md)
* [On Securing the Kubernetes Dashboard](https://blog.heptio.com/on-securing-the-kubernetes-dashboard-16b09b1b7aca)

## Platform binaries

> Verify platform binaries before deploying

✨ [Install and Set Up kubectl on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)

💡 Tips:

* Perform MD5 checks on binaries against [official releases](https://github.com/kubernetes/kubernetes/releases).

⚗️ [Practice](practice/1.6-platform-binaries.md)

📝 Read more:

* [Learn How to Generate and Verify Files with MD5 Checksum in Linux](https://www.tecmint.com/generate-verify-check-files-md5-checksum-linux/)
* [Ubuntu how-to sha256sum](https://help.ubuntu.com/community/HowToSHA256SUM).

---

🧵 Next: [Cluster hardening](2-cluster-hardening.md)
