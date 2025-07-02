
# Container Orchestration & Kubernetes Explained

## Table of Contents

1. [What is a Container Orchestration Platform?](#what-is-a-container-orchestration-platform)
2. [What is Kubernetes?](#what-is-kubernetes)
3. [Evolution of Kubernetes](#evolution-of-kubernetes)
4. [Kubernetes Architecture](#kubernetes-architecture)
   * [Control Plane (Master) Components](#control-plane-master-components)
   * [Worker Node Components](#worker-node-components)
5. [Kubernetes Objects (Ordered)](#kubernetes-objects-ordered)
   * [Pod](#pod)
   * [ReplicaSet](#replicaset)
   * [Deployment](#deployment)
   * [StatefulSet](#statefulset)
   * [Job](#job)
   * [ConfigMap](#configmap)
   * [Secret](#secret)
   * [PersistentVolume (PV)](#persistentvolume-pv)
   * [PersistentVolumeClaim (PVC)](#persistentvolumeclaim-pvc)
   * [StorageClass](#storageclass)
   * [Horizontal Pod Autoscaler (HPA)](#horizontal-pod-autoscaler-hpa)
   * [Vertical Pod Autoscaler (VPA)](#vertical-pod-autoscaler-vpa)
   * [Service & Its Types](#service--its-types)
6. [Useful kubectl Commands](#useful-kubectl-commands)
7. [Best Practices & Tips](#best-practices--tips)
8. [Resources](#resources)

---

## What is a Container Orchestration Platform?

A **Container Orchestration Platform** is a system that automates the deployment, scaling, networking, and lifecycle management of containers across a cluster of machines.

### Key Capabilities

* **Automated Scheduling**: Run containers on optimal nodes.
* **Scaling**: Dynamically adjust the number of containers.
* **Self-healing**: Detect failed containers and restart them.
* **Networking**: Manage communication between containers.
* **Service Discovery**: Enable containers to find each other.

### Popular Tools

* **Kubernetes**
* **Docker Swarm**
* **Apache Mesos**

---

## What is Kubernetes?

**Kubernetes** (aka **K8s**) is an open-source container orchestration platform developed by Google and donated to the **Cloud Native Computing Foundation (CNCF)**.

Kubernetes abstracts the underlying infrastructure and enables developers to:

* Deploy applications declaratively using YAML files
* Auto-scale and self-heal apps
* Perform rolling updates/rollbacks
* Manage large-scale microservices architectures

---

## Evolution of Kubernetes

| Year        | Milestone                                                        |
| ----------- | ---------------------------------------------------------------- |
| Early 2000s | Google used **Borg** internally for managing containers          |
| 2014        | Kubernetes open-sourced by Google                                |
| 2015        | Kubernetes v1.0 released; CNCF founded                           |
| 2016-2020   | Cloud-native ecosystem explodes (Helm, Prometheus, Istio)        |
| 2021+       | Kubernetes becomes industry standard for container orchestration |

### Why Kubernetes Dominates

* Massive community and vendor support
* Extensible APIs and ecosystem
* Works across cloud providers (AWS, Azure, GCP)
* Strong automation and resilience features

---

##  Kubernetes Architecture

Kubernetes uses a **master-worker** model, separating control operations from workload execution.

---

### Control Plane (Master) Components

| Component                   | Description                                                        |
| --------------------------- | ------------------------------------------------------------------ |
| **kube-apiserver**          | Frontend for the Kubernetes control plane; handles REST operations |
| **etcd**                    | Distributed key-value store holding cluster state                  |
| **kube-scheduler**          | Assigns Pods to Nodes based on resources and constraints           |
| **kube-controller-manager** | Manages controllers like Deployment, Replication, Node, etc.       |

---

### Worker Node Components

| Component             | Description                                        |
| --------------------- | -------------------------------------------------- |
| **kubelet**           | Communicates with the API server to run containers |
| **kube-proxy**        | Manages networking and forwards traffic to Pods    |
| **Container Runtime** | Runs containers (e.g., Docker, containerd, CRI-O)  |

---

## Kubernetes Objects (Ordered)

This section introduces **core Kubernetes objects** in the order they are typically used and created in real deployments.

---

### Pod

The **Pod** is the smallest deployable unit in Kubernetes and typically hosts one container (or a few tightly coupled ones).

#### Use Case:

* Standalone test applications
* Core building block for higher-level abstractions

#### YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: simple-pod
spec:
  containers:
    - name: nginx-container
      image: nginx
```

---

### ReplicaSet

Ensures a **specified number of pod replicas** are running at all times.

#### Use Case:

* Basic replication controller
* Managed by Deployments

####  YAML

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: nginx-rs
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx
```

---

### Deployment

A **Deployment** manages ReplicaSets and provides rolling updates and rollbacks.

#### Use Case:

* Web apps and APIs
* Autoscaling and updating services

#### YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx
```

---

### StatefulSet

Manages **stateful applications** with persistent identity and storage.

#### Use Case:

* Databases (MySQL, MongoDB)
* Stateful services like Kafka or Redis

#### YAML

```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: web
spec:
  serviceName: "nginx"
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx
          volumeMounts:
            - name: www
              mountPath: /usr/share/nginx/html
  volumeClaimTemplates:
    - metadata:
        name: www
      spec:
        accessModes: ["ReadWriteOnce"]
        resources:
          requests:
            storage: 1Gi
```

---

### Job

A **Job** runs a **one-time task** to completion.

#### Use Case:

* Batch processing
* Data migrations

#### YAML

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: hello-job
spec:
  template:
    spec:
      containers:
        - name: hello
          image: busybox
          command: ["echo", "Hello World"]
      restartPolicy: Never
```

---

### ConfigMap

Stores **non-sensitive** key-value pairs for configuration.

#### Use Case:

* Injecting environment variables
* App settings

#### YAML

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  ENV: production
  DEBUG: "false"
```

---

### Secret

Used to store **sensitive data** like credentials in base64-encoded format.

#### YAML

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: db-secret
type: Opaque
data:
  username: YWRtaW4=     # admin
  password: cGFzc3dvcmQ= # password
```

---

### PersistentVolume (PV)

A piece of storage in the cluster provisioned by an admin.

#### YAML

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: local-pv
spec:
  capacity:
    storage: 2Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
```

---

### PersistentVolumeClaim (PVC)

A **request for storage** by a user or Pod.

#### YAML

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: local-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

---

### StorageClass

Defines **how** storage is provisioned dynamically.

#### YAML

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: fast-storage
provisioner: kubernetes.io/aws-ebs
parameters:
  type: gp2
```

---

### Horizontal Pod Autoscaler (HPA)

Automatically scales pods based on **CPU or memory utilization**.

#### YAML

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: nginx-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: nginx-deployment
  minReplicas: 2
  maxReplicas: 5
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 50
```

---

### Vertical Pod Autoscaler (VPA)

Adjusts **resource requests and limits** based on historical usage.

> Requires VPA controller to be installed.

#### YAML

```yaml
apiVersion: autoscaling.k8s.io/v1
kind: VerticalPodAutoscaler
metadata:
  name: nginx-vpa
spec:
  targetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: nginx-deployment
  updatePolicy:
    updateMode: "Auto"
```

---

### Service & Its Types

Services expose Pods to other applications or external users.

#### Types of Services

| Type             | Use Case                     | Example                     |
| ---------------- | ---------------------------- | --------------------------- |
| **ClusterIP**    | Internal-only access         | Default                     |
| **NodePort**     | Expose on each node          | `nodePort: 30036`           |
| **LoadBalancer** | External cloud load balancer | GCP, AWS                    |
| **ExternalName** | Alias to external DNS        | `externalName: example.com` |

---

## Useful kubectl Commands

```bash
kubectl get all                      # View all resources
kubectl get pods,svc                 # View specific resource types
kubectl describe deployment <name>  # Describe a deployment
kubectl logs <pod-name>             # Get pod logs
kubectl exec -it <pod> -- /bin/sh   # Shell access to container
kubectl delete -f <file.yaml>       # Delete resources from a file
kubectl explain deployment          # Inline documentation
```

---

## Best Practices & Tips

* Use **`kubectl apply`** for idempotent resource creation
* Separate environments with **namespaces**
* Use **ConfigMaps and Secrets** to decouple configuration
* Use **Probes (liveness/readiness)** for production apps
* Monitor with **Prometheus**, manage configs with **Helm**

---

## Resources

* [Official Kubernetes Docs](https://kubernetes.io/docs/)
* [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
* [Play with Kubernetes (Lab)](https://labs.play-with-k8s.com/)
* [Katacoda Kubernetes Scenarios](https://katacoda.com/courses/kubernetes)
* [CNCF Cloud Native Landscape](https://landscape.cncf.io/)

---
