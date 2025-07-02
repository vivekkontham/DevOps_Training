# Docker & Containerization


## Table of Contents

1. [What is Containerization?](#what-is-containerization)
2. [Evolution of Containerization](#evolution-of-containerization)
3. [Types of Containerization Platforms](#types-of-containerization-platforms)
4. [Purpose of Containerization](#purpose-of-containerization)
5. [Benefits of Containerization](#benefits-of-containerization)
6. [What is Docker?](#what-is-docker)
7. [Why Docker?](#why-docker)
8. [Docker Architecture](#docker-architecture)
9. [Core Components of Docker](#core-components-of-docker)
10. [Docker Architecture Layers](#docker-architecture-layers)
11. [Docker Workflow](#docker-workflow)
12. [Common Docker Commands](#common-docker-commands)
13. [Further Reading](#further-reading)

---

## What is Containerization?

**Containerization** is the process of packaging software code, configurations, and dependencies into a single portable unit called a **container**. This unit can run consistently across environments such as development, testing, and production.

### Key Traits:

* Portable
* Lightweight
* Isolated from the host system

### Includes:

* App code
* Libraries
* Runtime
* System tools
* Config files

---

## Evolution of Containerization

| Era         | Technology                   | Description                                 |
| ----------- | ---------------------------- | ------------------------------------------- |
| 1979        | chroot (Unix)                | Isolated file systems                       |
| Early 2000s | Solaris Zones, FreeBSD Jails | OS-level virtualization                     |
| 2008–2013   | LXC (Linux Containers)       | Process isolation with cgroups & namespaces |
| 2013–Now    | Docker                       | Simplified container platform               |
| 2015+       | Kubernetes, containerd       | Large-scale orchestration and runtimes      |

---

## Types of Containerization Platforms

### 1. Container Engines

| Platform   | Description                    |
| ---------- | ------------------------------ |
| Docker     | Most popular engine            |
| containerd | Core container runtime         |
| CRI-O      | Lightweight Kubernetes runtime |
| Podman     | Daemonless Docker alternative  |

### 2. Orchestration Platforms

| Platform     | Description                        |
| ------------ | ---------------------------------- |
| Kubernetes   | Manages scaling and orchestration  |
| Docker Swarm | Native Docker orchestration        |
| Nomad        | Lightweight scheduler by HashiCorp |

### 3. Cloud-Native Platforms

| Platform      | Description                               |
| ------------- | ----------------------------------------- |
| AWS ECS/EKS   | Managed container and Kubernetes services |
| Azure AKS/ACI | Azure Kubernetes and container hosting    |
| Google GKE    | Managed Kubernetes on Google Cloud        |
| OpenShift     | Enterprise Kubernetes from Red Hat        |

---

## Purpose of Containerization

* Eliminate environment mismatch
* Streamline CI/CD
* Isolate services
* Enable microservices
* Scale horizontally with ease

---

## Benefits of Containerization

| Benefit                | Explanation                       |
| ---------------------- | --------------------------------- |
| Portability            | Runs anywhere with Docker runtime |
| Simplified DevOps      | Seamless integration with CI/CD   |
| Lightweight            | Minimal overhead compared to VMs  |
| Faster Startup         | Launches in milliseconds          |
| Reproducibility        | Same environment across lifecycle |
| Improved Security      | Isolated process execution        |
| Efficient Resource Use | Shares host OS kernel             |

---

## What is Docker?

**Docker** is an open-source containerization platform used to develop, ship, and run applications as lightweight containers. It simplifies application deployment across environments.

* Uses OS-level virtualization
* Empowers DevOps and CI/CD pipelines
* Built on Linux kernel features like namespaces and cgroups

---

## Why Docker?

* Eliminate "works on my machine" issues
* Lightweight alternative to virtual machines
* Accelerate development-to-production cycle
* Enhance security and control

---

## Docker Architecture

Docker follows a client-server model:

```
+-------------------+         +--------------------+
|   Docker Client   | <--->   |   Docker Daemon    |
+-------------------+         +--------------------+
                                  ^
                                  |
                         -------------------
                         |  Images / Volumes |
                         |  Containers        |
                         -------------------
```

---

## Core Components of Docker

### 1. Docker Client (`docker` CLI)

* It’s the interface you use in the terminal.
* Example: `docker run nginx`
* It sends commands to Docker Daemon through the REST API.

### 2. Docker Daemon (`dockerd`)

* A background process that listens for API requests and manages objects like containers, images, volumes, and networks.
* Automatically downloads images from registries if not present locally.

### 3. Docker Images

* These are **read-only templates** used to create containers.
* Built using a `Dockerfile`.

**Example Dockerfile:**

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "index.js"]
```

Build the image:

```bash
docker build -t my-node-app .
```

### 4. Docker Containers

* A container is a **runtime instance** of a Docker image.
* It contains everything needed to run the application.
* Isolated but uses the host OS kernel.

**Example:**

```bash
docker run -d -p 3000:3000 my-node-app
```

### 5. Docker Registries

* A storage and distribution system for Docker images.
* Examples: Docker Hub, GitHub Container Registry, AWS ECR

**Commands:**

```bash
docker login
docker push my-node-app:latest
docker pull nginx:alpine
```

### 6. Docker Volumes

* Used for persistent storage outside of containers.
* Volumes remain even after the container is removed.

**Example:**

```bash
docker volume create mydata

docker run -v mydata:/app/data my-node-app
```

### 7. Docker Networks

* Allow communication between containers or with external services.
* Default modes: `bridge`, `host`, `none`

**Example:**

```bash
docker network create mynet
docker run --network=mynet my-node-app
```

---

## Docker Architecture Layers

| Layer           | Description                                   |
| --------------- | --------------------------------------------- |
| Docker Client   | User-facing CLI tool                          |
| Docker Daemon   | Service managing images, containers, networks |
| Docker Host     | Local system resources (CPU, RAM, storage)    |
| Docker Registry | Remote image repositories                     |
| Kernel Features | Namespaces, cgroups, UnionFS                  |

---

## Docker Workflow

### Step-by-Step Java App Workflow Using Docker

1. **Create a Dockerfile for a Java App**

```dockerfile
FROM openjdk:17
WORKDIR /app
COPY target/hello-world.jar hello-world.jar
CMD ["java", "-jar", "hello-world.jar"]
```

2. **Build the Docker Image**

```bash
docker build -t my-java-app:1.0 .
```

3. **Tag the Image for Private Registry**

```bash
docker tag my-java-app:1.0 myregistry.com/my-java-app:1.0
```

4. **Login to Private Registry**

```bash
docker login myregistry.com
```

5. **Push the Image**

```bash
docker push myregistry.com/my-java-app:1.0
```

6. **Pull the Image on Target Server**

```bash
docker pull myregistry.com/my-java-app:1.0
```

7. **Run Container With Port and Volume**

```bash
docker volume create javadata

docker run -d \
  --name java-container \
  -p 8080:8080 \
  -v javadata:/app/data \
  myregistry.com/my-java-app:1.0
```

8. **Stop the Container**

```bash
docker stop java-container
```

9. **Restart the Container**

```bash
docker start java-container
```

10. **Remove the Container**

```bash
docker rm java-container
```

11. **Delete the Image**

```bash
docker rmi myregistry.com/my-java-app:1.0
```
---

## Common Docker Commands

```bash
docker pull nginx:latest                   # Pull an image from Docker Hub
docker build -t myapp:1.0 .                # Build image from Dockerfile
docker run -d -p 8080:80 myapp:1.0         # Run container in detached mode
docker ps                                  # List running containers
docker ps -a                               # List all containers
docker exec -it container_name sh          # Open shell inside container
docker stop container_id                   # Stop a running container
docker rm container_id                     # Remove a stopped container
docker rmi image_id                        # Remove a Docker image
docker inspect container_id                # Show detailed info (JSON)
docker logs container_id                   # View container logs
docker volume create data_volume           # Create persistent volume
docker volume ls                           # List volumes
docker volume rm data_volume               # Remove unused volume
docker tag image:tag repo/image:tag        # Tag image for another repo
docker login                               # Authenticate with Docker registry
```

---
## Further Reading

* [Docker Official Documentation](https://docs.docker.com)
* [Docker CLI Reference](https://docs.docker.com/engine/reference/commandline/docker/)
* [Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
* [Play with Docker](https://labs.play-with-docker.com)

---
