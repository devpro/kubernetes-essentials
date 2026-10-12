# Certified Kubernetes Administrator (CKA)

→ [cncf.io/certification/cka](https://www.cncf.io/training/certification/cka/)

## Advices

- Time flies really fast, go quickly
- Practice troubleshooting
- Get to know the [Kubernetes documentation](https://kubernetes.io/docs/home/)
- Have some experience with [BusyBox](https://busybox.net/) ([Docker image source](https://github.com/docker-library/busybox), [Playing with Busybox](https://docker-curriculum.com/#playing-with-busybox))

<details>
  <summary>Examples</summary>
  
  ```bash
  # Create a 1-pod deployment and expose the deployment with a service (see https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
  kubectl apply -f https://k8s.io/examples/controllers/nginx-deployment.yaml
  #kubectl create deployment nginx --image=nginx
  kubectl get deployments
  kubectl create service nodeport nginx --tcp=80:80
  kubectl get services
  curl master:30386
  curl node01:30386
  
  # Stand up a busybox:1.28 pod and do nslookup for both the Service and the Container
  kubectl run -i --tty busybox --image=busybox -- sh
  ```

</details>

- Create Kubernetes objects from the command line (no YAML)

<details>
  <summary>Examples</summary>
  
  ```bash
  kubectl create rolebinding john-admin-binding --clusterrole=admin --user=john --namespace=acme
  ```

</details>

- Know ways to interact with the container in the pod (see [Get a Shell to a Running Container](https://kubernetes.io/docs/tasks/debug-application-cluster/get-shell-running-container/) and [kubectl exec](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#exec))

<details>
  <summary>Examples</summary>
  
  ```bash
  kubectl get pod shell-demo
  kubectl exec --stdin --tty shell-demo -- /bin/bash
  kubectl exec shell-demo env
  ```

</details>

### Knowledge check

Be able to:

1. Take a snapshot of etcd data

<details>
  <summary>Answer 1</summary>

  TODO
</details>

1. Print out a list of all nodes that are Ready but not tainted with NoSchedule

<details>
  <summary>Answer 2</summary>

  TODO
</details>

### External notes

- [Study guide from AutSoft](https://blog.autsoft.hu/certified-kubernetes-administrator/)
- [Review from Rieckpil](https://rieckpil.de/review-ckad-certified-kubernetes-application-developer-program/)
- [David-VTUK/CKA-StudyGuide](https://github.com/David-VTUK/CKA-StudyGuide)

TODO :

- [Preparing for the Certified Kubernetes Administrator (CKA) Program](https://dzone.com/articles/preparing-for-the-certified-kubernetes-administrat?edition=542303&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202019-12-09)
- [Kubernetes Upgrade: The Definitive Guide to Do-It-Yourself](https://dzone.com/articles/kubernetes-upgrade-the-definitive-guide-to-do-it-yourself?edition=595298)
- [ismet55555/Certified-Kubernetes-Administrator-Notes](https://github.com/ismet55555/Certified-Kubernetes-Administrator-Notes)
