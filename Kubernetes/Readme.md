
## 🟢 Beginner Level: Core Concepts

### 1. **Kubernetes Architecture**
- Master components: `kube-apiserver`, `etcd`, `kube-scheduler`, `kube-controller-manager`, `kubelet`, `kube-proxy`
- Understand the role of **Master** and **Worker** nodes

### 2. **Pods and Containers**
- What is a Pod?
- Multi-container Pods
- Pod lifecycle and restart policies

### 3. **Deployments and ReplicaSets**
- Creating and managing Deployments
- Rolling updates and rollbacks
- Scaling applications

### 4. **Services**
- ClusterIP, NodePort, LoadBalancer
- Service discovery and DNS

### 5. **Namespaces**
- Logical separation of resources
- Resource quotas and limits

### 6. **ConfigMaps and Secrets**
- Injecting configuration into Pods
- Managing sensitive data securely

---

## 🟡 Intermediate Level: Operational and DevOps Focus

### 7. **Volumes and Persistent Storage**
- EmptyDir, hostPath, PersistentVolume (PV), PersistentVolumeClaim (PVC)
- StorageClasses and dynamic provisioning

### 8. **Helm**
- Helm charts for packaging applications
- Helm templating and values files
- Helm 3 vs Helm 2

### 9. **Networking**
- CNI plugins (Calico, Flannel)
- Network Policies
- Ingress Controllers (NGINX, Traefik)

### 10. **Resource Management**
- CPU and memory requests/limits
- Horizontal Pod Autoscaler (HPA)
- Vertical Pod Autoscaler (VPA)

### 11. **Monitoring and Logging**
- Prometheus + Grafana for metrics
- Fluentd/Fluent Bit, ELK stack for logs
- Kubernetes events and audit logs

### 12. **RBAC and Security**
- Role-Based Access Control (RBAC)
- Service Accounts and IAM integration
- Pod Security Standards (PSS)

### 13. **CI/CD Integration**
- GitOps with ArgoCD or Flux
- Jenkins, GitLab CI, or GitHub Actions with Kubernetes
- Canary and Blue/Green deployments

---

https://spacelift.io/blog/prometheus-kubernetes
