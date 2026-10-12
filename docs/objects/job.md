# Kubernetes Job object

A [**Job**](https://kubernetes.io/docs/concepts/workloads/controllers/job/) creates one or more Pods and ensures that a specified number of them successfully terminate.
As pods successfully complete, the Job tracks the successful completions.
When a specified number of successful completions is reached, the task (ie, Job) is complete.
Deleting a Job will clean up the Pods it created.

## Manifest examples

- Displaying PI

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: pi-with-timeout
spec:
  backoffLimit: 5
  activeDeadlineSeconds: 100
  template:
    spec:
      containers:
        - name: pi
          image: perl
          command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
      restartPolicy: Never
```

- Execute 5 times, 2 at a times maximum, a busybox container that will wait for 3 seconds

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: sleepy
spec:
  completions: 5
  parallelism: 2
  template:
    spec:
      containers:
        - name: resting
          image: busybox
          command: ["/bin/sleep"]
          args: ["3"]
      restartPolicy: Never
```
