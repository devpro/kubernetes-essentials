# seccomp

> Seccomp stands for secure computing mode and has been a feature of the Linux kernel since version 2.6.12. It can be used to sandbox the privileges of a process, restricting the calls it is able to make from userspace into the kernel. Kubernetes lets you automatically apply seccomp profiles loaded onto a node to your Pods and containers.
>
> &mdash; _[kubernetes.io/docs/tutorials/security/seccomp](https://kubernetes.io/docs/tutorials/security/seccomp/)_

✨ [Pod Security Context](https://kubernetes.io/docs/reference/kubernetes-api/workload-resources/pod-v1/#security-context-1), [Set the Seccomp Profile for a Container](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/#set-the-seccomp-profile-for-a-container),
[Enable seccomp for all workloads with a new v1.22 alpha feature](https://kubernetes.io/blog/2021/08/25/seccomp-default/), [Finding suspicious syscalls with the seccomp notifier](https://kubernetes.io/blog/2022/12/02/seccomp-notifier/)

🌐 [Kernel documentation](https://www.kernel.org/doc/Documentation/prctl/seccomp_filter.txt), [A seccomp overview by Jake Edge](https://lwn.net/Articles/656307/), [Seccomp security profiles for Docker](https://docs.docker.com/engine/security/seccomp/)
