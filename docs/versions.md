# Versions

[Release notes](https://relnotes.k8s.io/)

## v1.34

* [DRA (Dynamic Resource Allocation) Consumable Capacity](https://kubernetes.io/blog/2025/09/18/kubernetes-v1-34-dra-consumable-capacity/)

## v1.32 (Penelope)

* [Announcement](https://kubernetes.io/blog/2024/12/11/kubernetes-v1-32-release/) - December 11, 2024
* [Sysdig What's new](https://www.sysdig.com/blog/kubernetes-1-32-whats-new) - December 5, 2024
* Enhancements promoted to Stable:
  * Structured Authorization Configuration
  * Bound service account token improvements
  * Custom Resource Field Selectors
  * Retry Generate Name
  * Make Kubernetes aware of the LoadBalancer behaviour
  * Field status.hostIPs added for Pod
  * [Custom profile in kubectl debug](https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/#custom-profile)
  * Memory Manager
  * Support to size memory backed volumes
  * Improved multi-numa alignment in Topology Manager
  * Add job creation timestamp to job annotations
  * Add Pod Index Label for StatefulSets and Indexed Jobs
  * Auto remove PVCs created by StatefulSet

## v1.26 (Electrifying)

* [Announcement](https://kubernetes.io/blog/2022/12/09/kubernetes-v1-26-release/) - December 09, 2022
* [Sysdig What's new](https://sysdig.com/blog/kubernetes-1-26-whats-new) - November 30, 2022
* Main changes
  * [Introducing Validating Admission Policies](https://kubernetes.io/blog/2022/12/20/validating-admission-policies-alpha/)
  * [GA Support for Kubelet Credential Providers](https://kubernetes.io/blog/2022/12/22/kubelet-credential-providers/)

## v1.25 (Combiner)

* [Announcement](https://kubernetes.io/blog/2022/08/23/kubernetes-v1-25-release/) - August 23, 2022
* Major Themes
  * Pod Security Admission (PodSecurityPolicy is removed)
  * [Ephemeral Containers](https://kubernetes.io/docs/concepts/workloads/pods/ephemeral-containers/)
  * Support for [cgroups v2](https://kubernetes.io/docs/concepts/architecture/cgroups/)
  * endPort in Network Policy

## 1.23

* [CNCF Live Webinar](https://community.cncf.io/events/details/cncf-cncf-online-programs-presents-cncf-live-webinar-kubernetes-123-release/) - January 4, 2022
* [Sysdig What's new](https://sysdig.com/blog/kubernetes-1-23-whats-new/) - November 30, 2021
* [Kubernetes Podcast from Google with Rey Lejano](https://kubernetespodcast.com/episode/167-kubernetes-1.23/) - December 8, 2021

## 1.22

* Annoucement: [Kubernetes 1.22: Reaching New Peaks](https://kubernetes.io/blog/2021/08/04/kubernetes-1-22-release-announcement/) - August 04, 2021
* CNCF Live Webinar: [Kubernetes 1.22 release](https://community.cncf.io/events/details/cncf-cncf-online-programs-presents-cncf-live-webinar-kubernetes-122-release/) - October 5, 2021
* Sysdig: [Kubernetes 1.22 – What’s new?](https://sysdig.com/blog/kubernetes-1-22-whats-new/) - July 29, 2021

## 1.21

→ [Kubernetes 1.21: Power to the Community](https://kubernetes.io/blog/2021/04/08/kubernetes-1-21-release-announcement/) - April 08, 2021

### 1.21 Content

* [Introducing Suspended Jobs](https://kubernetes.io/blog/2021/04/12/introducing-suspended-jobs/) - April 12, 2021
* [Introducing Indexed Jobs](https://kubernetes.io/blog/2021/04/19/introducing-indexed-jobs/) - April 19, 2021
* [PodSecurityPolicy Deprecation: Past, Present, and Future](https://kubernetes.io/blog/2021/04/06/podsecuritypolicy-deprecation-past-present-and-future/) - April 06, 2021

### 1.21 Articles & webinars

* [CNCF Live Webinar: Kubernetes 1.21 Release](https://community.cncf.io/events/details/cncf-cncf-online-programs-presents-cncf-live-webinar-kubernetes-121-release/) - May 20, 2021
* [sysdig - Kubernetes 1.21 – What’s new?](https://sysdig.com/blog/kubernetes-1-21-whats-new) - March 31, 2021

## 1.20

[Kubernetes 1.20: The Raddest Release](https://kubernetes.io/blog/2020/12/08/kubernetes-1-20-release-announcement/)

## 1.19

[Kubernetes 1.19: Accentuate the Paw-sitive](https://kubernetes.io/blog/2020/08/26/kubernetes-release-1.19-accentuate-the-paw-sitive/)

[Kubernetes 1.19: CNCF Webinar](https://www.cncf.io/webinars/kubernetes-1-19/)

1. Support for Kubernetes will be increased from 9 months (or 3 releases) to one year (stable)

2. There is a defined process on how API transition from Beta to GA (stable)

3. The API server will include a warning header when you use deprecated APIs (beta)

4. ".status.conditions" is standardised across objects (stable)

5. Standardise on "http://node-role.kubernetes.io" label (beta)

6. Removed the beta APIs from the conformance tests (beta)

7. Support CRI-ContainerD on Windows (beta)

8. The process to obtain the kubelet certificate and rotate it as its expiration date approaches is now stable

9. NodeRestriction admission plugin prevents Kubelets from self-setting labels within core namespaces (stable)

10. The Certificates API includes a Registration Authority to provision certificates for non-core uses (stable)

11. New kubeadm component config scheme aimed at customisable default for kubelets and core components (alpha)

12. You can include patched to your Kubeadm config (alpha)

13. A standard structure for Kubernetes log messages (alpha)

14. Redesign Event API (stable)

15. Ingress graduates to V1 (stable)

16. The new EndpointSlice API will split endpoints into several Endpoint Slice resources (beta)

17. The EndpointSlice API added a new AppProtocol field to allow application protocols to be specified for each port (beta)

18. SCTP is now supported as an additional protocol alongside TCP and UDP in Pod, Service, Endpoint, and NetworkPolicy (beta)

19. It is possible to set a pod’s hostname to its Fully Qualified Domain Name (FQDN) (alpha)

20. The Kubelet isn't expected to gather metrics anymore. This is delegated to the PodResources API (alpha)

21. The node topology manager is a kubelet component that centralizes the coordination of hardware resource assignments (beta)

22. Seccomp provides sandboxing, it reduces the actions that a process can perform which reduces a system potential attack surface (stable)

23. You can build Kubelet without Docker (stable)

24. You can define a global defaultConstraints that will be applied at cluster level to all of the pods that don’t define their own topologySpreadConstraints (alpha)

25. ComponentConfig is an ongoing effort to make component configuration more dynamic (beta)

26. With topologySpreadConstraints, you can define rules to distribute your pods evenly across your multi-zone cluster, so high availability will work correctly and the resource utilization will be efficient (beta)

27. With "PreemptionPolicy: Never" Pods can be placed in the scheduling queue ahead of lower-priority pods, but they cannot preempt other pods (beta)

28. You can run the scheduler with multiple Scheduling Profiles (beta)

29. New API for generic ephemeral inline volumes (alpha)

30. Storage Capacity Tracking prevents pods to be scheduled on nodes connected to CSI volumes without enough free space available (alpha)

31. CSI drivers can opt-in to volume ownership change (alpha)

32. Immutable Secrets and ConfigMaps (beta)

33. Azure disk in-tree driver is moved to CSI (beta)

34. vSphere disk in-tree driver is moved to CSI (beta)

[sysdig - What’s new in Kubernetes 1.19?](https://sysdig.com/blog/whats-new-kubernetes-1-19/)

## 1.18

[Kubernetes 1.18: Fit & Finish](https://kubernetes.io/blog/2020/03/25/kubernetes-1-18-release-announcement/)

## 1.17

[Kubernetes 1.17: Stability](https://kubernetes.io/blog/2019/12/09/kubernetes-1-17-release-announcement/) - Dec 09 '19

[StackRox - What’s New in Kubernetes 1.17: A Deeper Look at New Features](https://www.stackrox.com/post/2019/12/whats-new-in-kubernetes-1.17-a-deeper-look-at-new-features/) - Dec 09 '19
