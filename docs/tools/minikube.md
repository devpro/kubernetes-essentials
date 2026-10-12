# Minikube

> Local Kubernetes, focused on application development & education

[minikube.sigs.k8s.io](https://minikube.sigs.k8s.io/), [kubernetes/minikube](https://github.com/kubernetes/minikube)

## Quick start

### Installation

Follow the instructions given in the [Getting Started page](https://minikube.sigs.k8s.io/docs/start/).

More information on [Installing Kubernetes with Minikube page](https://kubernetes.io/docs/setup/learning-environment/minikube/).

Make sure Docker Desktop has allocated at least 3 Go of RAM.

### Run/stop

**Important**: If you're on Windows, open a command window as admin.

Run:

- (Optional) `minikube config set vm-driver hyperv` to set the default driver (here [Hyper-V driver](https://minikube.sigs.k8s.io/docs/reference/drivers/hyperv/))
- `minikube start` to start the Kubernetes node
- `minikube status` to get the overall status
- `minikube pause` to pause it
- `minikube stop` to stop it

### Dashboard

Run `minikube dashboard` to open the web dashboard.

### Kubernetes CLI

Run `kubectl config use-context minikube` to be able to use kubectl on your local Kubernetes instance.

## CLI reference

[Documentation](https://minikube.sigs.k8s.io/docs/commands/)

Command | Action
------- | ------
`minikube service hello-minikube` | Maunch a web browser on a service
`minikube service xxx --url` | Display url for a given service (xxx)
`minikube config set memory 16384` | Update default memory limit (2048 by default)
`minikube addons list` | Browse the catalog of easily installed Kubernetes services
`minikube tunnel` | Start a tunnel to create a routable IP for a "balanced" deployment
`minikube start -p aged --kubernetes-version=v1.16.1` | Create another cluster running an older Kubernetes release
`minikube ip` | Display Kubernetes IP

### Clean-up

Run `minikube delete` and, if needed, delete the `.kube` and `.minikube` folder in your home directory.

## Extensions

```bash
# Enable metrics-server (https://github.com/kubernetes-sigs/metrics-server)
minikube addons enable metrics-server
kubectl get apiservices
```

## Known issues

- Incorrect date (can lead to errors with Docker pull)

```bash
minikube ssh -- date
minikube ssh
date --set "12 Aug 2020 17:20:00"
exit
minikube ssh -- docker run -i --rm --privileged --pid=host debian nsenter -t 1 -m -u -n -i date -u $(date -u +%m%d%H%M%Y)
minikube ssh -- date
```
