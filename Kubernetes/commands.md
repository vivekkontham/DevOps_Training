
---

# 🧰 **kubectl Cheat Sheet**

---

## 📦 **Basic Commands**

| Action                        | Command                             |
| ----------------------------- | ----------------------------------- |
| Show cluster info             | `kubectl cluster-info`              |
| Show current context          | `kubectl config current-context`    |
| List all contexts             | `kubectl config get-contexts`       |
| Switch context                | `kubectl config use-context <name>` |
| Get client and server version | `kubectl version --short`           |

---

## 📄 **Working with Resources**

| Action                   | Command                          |
| ------------------------ | -------------------------------- |
| List all resources       | `kubectl get all`                |
| List pods                | `kubectl get pods`               |
| List deployments         | `kubectl get deployments`        |
| List services            | `kubectl get svc`                |
| Describe a resource      | `kubectl describe pod <name>`    |
| Show YAML for a resource | `kubectl get pod <name> -o yaml` |
| Apply config from YAML   | `kubectl apply -f <file>.yaml`   |
| Delete a resource        | `kubectl delete -f <file>.yaml`  |
| Delete by type/name      | `kubectl delete pod <name>`      |

---

## 👨‍🔧 **Pods**

| Action                  | Command                                       |
| ----------------------- | --------------------------------------------- |
| Create a pod from image | `kubectl run <name> --image=<image>`          |
| Exec into pod           | `kubectl exec -it <pod-name> -- /bin/bash`    |
| Port forward            | `kubectl port-forward <pod-name> 8080:80`     |
| Logs from pod           | `kubectl logs <pod-name>`                     |
| Logs from a container   | `kubectl logs <pod-name> -c <container-name>` |

---

## ⚙️ **Deployments**

| Action               | Command                                                         |
| -------------------- | --------------------------------------------------------------- |
| Create from file     | `kubectl apply -f deployment.yaml`                              |
| Scale deployment     | `kubectl scale deployment <name> --replicas=5`                  |
| Update image         | `kubectl set image deployment/<name> <container>=<image>:<tag>` |
| Rollback deployment  | `kubectl rollout undo deployment <name>`                        |
| Check rollout status | `kubectl rollout status deployment <name>`                      |

---

## 🧪 **Debugging & Troubleshooting**

| Action                  | Command                                                    |
| ----------------------- | ---------------------------------------------------------- |
| Describe resource       | `kubectl describe <type> <name>`                           |
| Check pod logs          | `kubectl logs <pod-name>`                                  |
| Get pod events          | `kubectl get events --sort-by=.metadata.creationTimestamp` |
| Run diagnostics command | `kubectl exec -it <pod-name> -- <command>`                 |

---

## 🔒 **Namespaces**

| Action                | Command                                                   |
| --------------------- | --------------------------------------------------------- |
| List namespaces       | `kubectl get ns`                                          |
| Set default namespace | `kubectl config set-context --current --namespace=<name>` |
| Create namespace      | `kubectl create ns <name>`                                |
| Delete namespace      | `kubectl delete ns <name>`                                |

---

## 🔍 **Useful Flags**

| Flag             | Description         |
| ---------------- | ------------------- |
| `-n <namespace>` | Specify namespace   |
| `-o wide`        | Show more details   |
| `-o yaml/json`   | Output in YAML/JSON |
| `--watch`        | Watch updates live  |

---

## 📂 **Working with ConfigMaps and Secrets**

| Action           | Command                                                         |
| ---------------- | --------------------------------------------------------------- |
| Create ConfigMap | `kubectl create configmap <name> --from-literal=key=value`      |
| View ConfigMap   | `kubectl get configmap <name> -o yaml`                          |
| Create Secret    | `kubectl create secret generic <name> --from-literal=key=value` |
| View Secret      | `kubectl get secret <name> -o yaml`                             |

---
