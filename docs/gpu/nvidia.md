# NVIDIA Cloud Native

[docs](https://docs.nvidia.com/datacenter/cloud-native/contents.html), [youtube](https://www.youtube.com/@NVIDIA), [youtube developer](https://www.youtube.com/@NVIDIADeveloper)

## Graphical cards

Name | Specifications | Comments
-----|----------------|-----------
T4   |                |
T400 |                | Affordable
V100 |                |
A100 |                |

## GPUs on Kubernetes

* [Install Kubernetes](https://docs.nvidia.com/datacenter/cloud-native/kubernetes/install-k8s.html)
* [Improving GPU Utilization in Kubernetes](https://developer.nvidia.com/blog/improving-gpu-utilization-in-kubernetes/)
* [On Demand Webinar](https://info.nvidia.com/how-to-use-gpus-on-kubernetes-webinar.html)

## NVIDIA Multi-Instance GPU (MIG)

> Multi-Instance GPU (MIG) expands the performance and value of NVIDIA H100, A100, and A30 Tensor Core GPUs. MIG can partition the GPU into as many as seven instances, each fully isolated with its own high-bandwidth memory, cache, and compute cores.

→ [product](https://www.nvidia.com/en-us/technologies/multi-instance-gpu/)

## NVIDIA GPU Cloud (NGC)

* [NGC catalog](https://catalog.ngc.nvidia.com/containers)

## Components

### NVIDIA Container Runtime

→ [code](https://github.com/NVIDIA/nvidia-container-runtime)

### NVIDIA Container Toolkit

→ [code](https://github.com/NVIDIA/nvidia-docker)

### NVIDIA DCGM-Exporter

> DCGM-Exporter exposes GPU metrics exporter for Prometheus leveraging [NVIDIA Data Center GPU Manager (DCGM)](https://developer.nvidia.com/dcgm)

→ [code](https://github.com/NVIDIA/dcgm-exporter), [docs](https://docs.nvidia.com/datacenter/cloud-native/gpu-telemetry/dcgm-exporter.html)

### NVIDIA GPU feature discovery

→ [code](https://github.com/NVIDIA/gpu-feature-discovery)

### NVIDIA GPU Operator

→ [code](https://github.com/NVIDIA/gpu-operator), [docs](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/overview.html)

* [Platform suppport](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/platform-support.html)
* [Getting support](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/getting-started.html)

### NVIDIA Device Plugin

→ [code](https://github.com/NVIDIA/k8s-device-plugin)

## Tutorials

### NVIDIA GPU Operator in K3s

* [Installing & Using the NVIDIA GPU Operator in K3s with Rancher](https://www.virtualthoughts.co.uk/2022/11/21/installing-using-the-nvidia-gpu-operator-in-k3s-with-rancher/) by Virtual Thoughts - November 21, 2022

### NVIDIA GPUs with SLES

ℹ Full official support should come in early 2023

* Build and push a driver image for SLES (from [GitLab project](https://gitlab.com/nvidia/container-images/driver))

```bash
git clone https://gitlab.com/nvidia/container-images/driver.git && cd sle15

docker build . -t path/to/your/repo/driver:515.65.01-sles15.3 \
  --build-arg DRIVER_VERSION=515.65.01 \
  --build-arg CUDA_VERSION=11.7.1 \
  --build-arg SLES_VERSION=15.3

docker push path/to/your/repo/driver:515.65.01-sles15.3
```

* Deploy GPU Operator and specify custom driver image

```bash
helm install gpu-operator nvidia/gpu-operator \
  --create-namespace -n gpu-operator \
  --set driver.repository=path/to/your/repo
```
