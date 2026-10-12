# CKS (Certified Kubernetes Security Specialist)

You'll find here everything to know for the CKS exam. It has been written in December 2023, with the intention to be straight to the point.

## About the exam

> The program provides assurance that a CKS has the skills, knowledge, and competence on a broad range of best practices for securing container-based applications and Kubernetes platforms during build, deployment and runtime.
>
> &mdash; <cite>[training.linuxfoundation.org/certification](https://training.linuxfoundation.org/certification/certified-kubernetes-security-specialist/)</cite>

🚩 A valid CKA certification is required to try this exam

🌐 [Training Portal (Linux Foundation)](https://trainingportal.linuxfoundation.org/learn/dashboard), [PSI Exams Portal](https://test-takers.psiexams.com/linux/manage/my-tests), [Exam Instructions](https://docs.linuxfoundation.org/tc-docs/certification/important-instructions-cks)

## Curriculum

* [1. Cluster setup](1-cluster-setup.md)
* [2. Cluster hardening](2-cluster-hardening.md)
* [3. System hardening](3-system-hardening.md)
* [4. Minimize microservice vulnerabilities](4-minimize-microservice-vulnerabilities.md)
* [5. Supply chain security](5-supply-chain-security.md)
* [6. Monitoring, logging and runtime security](6-monitoring-logging-runtime-security.md)

## Examination resources

### Allowed websites

| Component      | Links                                                                                                            |
| -------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Kubernetes** | [kubernetes.io/docs](https://kubernetes.io/docs/), [kubernetes.io/blog](https://kubernetes.io/blog/)             |
| **etcd**       | [etcd.io/docs](https://etcd.io/docs/)                                                                            |
| **AppArmor**   | [gitlab.com/apparmor/apparmor/-/wikis/Documentation](https://gitlab.com/apparmor/apparmor/-/wikis/Documentation) |
| **Falco**      | [falco.org/docs](https://falco.org/docs/)                                                                        |
| **Trivy**      | [aquasecurity.github.io/trivy](https://aquasecurity.github.io/trivy/)                                            |

📌 Source: [Resources Allowed: All LF Certification Programs](https://docs.linuxfoundation.org/tc-docs/certification/certification-resources-allowed#certified-kubernetes-security-specialist-cks)

### Command line

✨ [`kubectl` cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/), [`kubectl` reference](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands), [`crictl` for debugging](https://kubernetes.io/docs/tasks/debug/debug-cluster/crictl/)

⚗️ Refresher: [Linux](practice/0.1-linux-commands.md), [Kubernetes](practice/0.2-kubernetes-commands.md)

### Copy/paste

Always works (but slow): copy/paste right mouse context menu actions

In the Terminal: `Ctrl`+`Shift`+`C` and `Ctrl`+`Shift`+`V`

Other apps like Firefox: `Ctrl`+`C` and `Ctrl`+`V`

In the Terminal also: mark text with the mouse and then press the mouse-middle key to insert (only works while staying in the Terminal)

You can try with this [Killercoda scenario](https://killercoda.com/kimwuestkamp/scenario/cks-cka-ckad-remote-desktop).

## General documentation

* Kubernetes
  * [Pod Security Standards](https://kubernetes.io/docs/concepts/security/pod-security-standards/)
  * [Policies](https://kubernetes.io/docs/concepts/policy/)
  * [Securing a Cluster](https://kubernetes.io/docs/tasks/administer-cluster/securing-a-cluster/)
* Kubernetes blog
  * [11 Ways (Not) to Get Hacked](https://kubernetes.io/blog/2018/07/18/11-ways-not-to-get-hacked/)
* AWS
  * [EKS best practices guide for security](https://aws.github.io/aws-eks-best-practices/security/docs/)
* Google Cloud
  * [GKE security overview](https://cloud.google.com/kubernetes-engine/docs/concepts/security-overview)
  * [Harden your GKE cluster's security](https://cloud.google.com/kubernetes-engine/docs/how-to/hardening-your-cluster)

## Training

* ✅ **A Cloud Guru**: [CKS](https://learn.acloud.guru/course/certified-kubernetes-security-specialist/dashboard) ([code](https://github.com/linuxacademy/content-cks-resources))
* **A Cloud Guru**: [Kubernetes Security](https://learn.acloud.guru/course/7d2c29e7-cdb2-4f44-8744-06332f47040e/dashboard)
* **KodeKloud**: [CKS](https://kodekloud.com/courses/certified-kubernetes-security-specialist-cks/) ([Course notes](https://github.com/kodekloudhub/certified-kubernetes-security-specialist-cks-course))
* **LinkedIn Learning**: [Securing Containers and Kubernetes Ecosystem](https://www.linkedin.com/learning/securing-containers-and-kubernetes-ecosystem/protect-your-containers-and-kubernetes-ecosystem)
* ~~**Linux Foundation**: [Kubernetes Security Essentials (LFS260)](https://training.linuxfoundation.org/training/kubernetes-security-essentials-lfs260/)~~ (doesn't help passing the certification)
* O'Reilly: [CKS certification guide](https://learning.oreilly.com/certifications/guides/Certified-Kubernetes-Security-Specialist-(CKS)/0636920886143/)
* **Udemy**: [CKS 2023](https://www.udemy.com/course/certified-kubernetes-security-specialist/?referralCode=D9329DEE203E7FEBE86B&couponCode=K8S-CKS-22)

## Tools

| Name                                       | Paragraph                                                                                 | Kubernetes definition                                        |
| ------------------------------------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| [AppArmor](tools/apparmor.md)              | [3.4 Kernel hardening](3-system-hardening.md#kernel-hardening)                            | annotations.`container.apparmor.security.beta.kubernetes.io` |
| [etcd](tools/etcd.md)                      |                                                                                           |                                                              |
| [Falco](tools/falco.md)                    | [6.1 Behavioral analytics](6-monitoring-logging-runtime-security.md#behavioral-analytics) |                                                              |
| [gVisor](tools/gvisor.md)                  | [4.3 Sandboxes](4-minimize-microservice-vulnerabilities.md#sandboxes)                     | spec.`runtimeClassName`                                      |
| [Kata Containers](tools/katacontainers.md) | [4.3 Sandboxes](4-minimize-microservice-vulnerabilities.md#sandboxes)                     | spec.`runtimeClassName`                                      |
| [kube-bench](tools/kube-bench.md)          | [1.2 CIS benchmark](1-cluster-setup.md#cis-benchmark)                                     |                                                              |
| [OPA Gatekeeper](tools/opa-gatekeeper.md)  | [4.1 Security domains](4-minimize-microservice-vulnerabilities.md#security-domains)       | `ConstraintTemplate`                                         |
| [seccomp](tools/seccomp.md)                | [3.4 Kernel hardening](3-system-hardening.md#kernel-hardening)                            | securityContext.`seccompProfile`                             |
| [SELinux](tools/selinux.md)                |                                                                                           | securityContext.`seLinuxOptions`                             |
| [Trivy](tools/trivy.md)                    | [5. Supply chain security](5-supply-chain-security.md#workload-static-analysis)           |                                                              |

## Free lab platforms

💡 CKS exam gives access to 2 sessions with [Killer Shell](https://github.com/killer-sh/cks-course-environment) ([example](practice/9.1-exam-cks-simulator.md))

* [CKS CLI](https://cks.kubernetes.tn/)
* [Cloud Native Security Tutorial](https://tutorial.kubernetes-security.info/)
* ✅ [Killercoda](https://killercoda.com/killer-shell-cks)
* ✅ [KodeKloud CKS Challenges](https://kodekloud.com/courses/cks-challenges/)
* [Kubernetes Goat](https://madhuakula.com/kubernetes-goat/)

## Other resources

### Documents

* [CNCF Cloud Native Security Whitepaper](https://github.com/cncf/tag-security/tree/main/security-whitepaper)
  * [PDF file (2022-05)](https://github.com/cncf/tag-security/blob/main/security-whitepaper/v2/CNCF_cloud-native-security-whitepaper-May2022-v2.pdf)
* [NSA, CISA release Kubernetes Hardening Guidance](https://www.nsa.gov/Press-Room/News-Highlights/Article/Article/2716980/nsa-cisa-release-kubernetes-hardening-guidance/) - March 15, 2022
  * [PDF file (2022-08)](https://media.defense.gov/2022/Aug/29/2003066362/-1/-1/0/CTR_KUBERNETES_HARDENING_GUIDANCE_1.2_20220829.PDF)
* [Sysdig Kubernetes Security Guide](https://sysdig.com/s-kubernetes-security-guide/)

### Study notes

* [Jayendra Patil - CKS learning path](https://jayendrapatil.com/certified-kubernetes-security-specialist-cks-learning-path/) ([Kubernetes exercises](https://github.com/jayendrapatil/kubernetes-exercises))
* [Scott Hawkins](https://github.com/echoboomer/k8s-cks-notes)

<!-- TODO: https://github.com/ruzickap/cks-notes -->

### Exam question examples

* [Benjamin Muschko](https://github.com/bmuschko/cks-crash-course)
* [Jaxon](https://github.com/theJaxon/CKS)
* [Mohamed Abukar](https://github.com/moabukar/CKS-Exercises-Certified-Kubernetes-Security-Specialist)
* [Viktar Mikalayeu](https://github.com/ViktorUJ/cks/tree/master/tasks/cks/labs)

### Videos

* [CKS KodeKloud Mock Exam 1 - Learn With GGS](https://www.youtube.com/watch?v=7eH7vfT0axA&list=PLglXbBWxN2H9-ATq0ShHVlMWskhRgvdJz) - Dec 6, 2021
* [Kubesimplify - Kubernetes security concepts and demos](https://youtu.be/VjlvS-qiz_U) - September 25, 2020
* [CNCF Tutorial - Getting Started With Cloud Native Security](https://youtu.be/MisS3wSds40) - September 4, 2020
* [Kubernetes Forum Seoul 2019 - Kubernetes Security Best Practices](https://youtu.be/wqsUfvRyYpw) - Dec 10, 2019
* [Code in Action - Learn Kubernetes Security](https://www.youtube.com/playlist?list=PLeLcvrwLe1859Rje9gHrD1KEp4y5OXApB) - Jul 8, 2020
* [Spectro Cloud Webinar - Certified Kubernetes Security Specialist](https://www.youtube.com/watch?v=Qqoe-PbuQcs) - May 4, 2022
