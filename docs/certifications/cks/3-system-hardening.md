# System hardening

## OS footprint

> Minimize host OS footprint (reduce attack surface)

✨ [Preventing containers from loading unwanted kernel modules](https://kubernetes.io/docs/tasks/administer-cluster/securing-a-cluster/#preventing-containers-from-loading-unwanted-kernel-modules)

💡 Tips:

* Careful with PodSpec `hostPID`, `hostIPC` and `hostNetwork`, and `securityContext.privileged` flags.

📝 Read more:

* [CIS Benchmarks](https://www.cisecurity.org/benchmark)
  * [Distribution Independent Linux](https://www.cisecurity.org/benchmark/distribution_independent_linux/)
  * [Ubuntu Linux](https://www.cisecurity.org/benchmark/ubuntu_linux)
* [Kubernetes Security Practices You Should Follow, by Sonatype](https://blog.sonatype.com/kubesecops-kubernetes-security-practices-you-should-follow) - August 29, 2019

## IAM roles

> Minimize IAM (Identity and Access Management) roles

⚡️ Notes:

* Principle of least privilege

📝 Read more:

* [AWS Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
* [Azure Best practices for Azure RBAC](https://learn.microsoft.com/en-us/azure/role-based-access-control/best-practices)
* [Google Cloud Use IAM securely](https://cloud.google.com/iam/docs/using-iam-securely)

## External access

> Minimize external access to the network

📝 Read more:

* [Amazon EC2 security groups for Linux instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)
* [Amazon EKS security group considerations](https://docs.aws.amazon.com/eks/latest/userguide/sec-group-reqs.html)
* [AWS Control traffic to subnets using network ACLs (Access Control List)](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)
* [Azure Security concepts for applications and clusters in AKS](https://learn.microsoft.com/en-us/azure/aks/concepts-security)
* [Managing firewalls with UFW on Kubernetes](https://community.replicated.com/t/managing-firewalls-with-ufw-on-kubernetes/230)
* [IP Tables (iptables) Cheat Sheet](https://gist.github.com/davydany/0ad377f6de3c70056d2bd0f1549e1017)

## Kernel hardening

> Appropriately use kernel hardening tools such as AppArmor, seccomp  

⚗️ [Practice](practice/3.4-kernel-hardening.md)

🚀 [AppArmor](tools/apparmor.md), [seccomp](tools/seccomp.md)

---

🧵 Next: [Minimize microservice vulnerabilities](4-minimize-microservice-vulnerabilities.md)
