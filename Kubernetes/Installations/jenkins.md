# Jenkins Installation using Helm on Kubernetes

````markdown

## Prerequisites

- A running Kubernetes cluster (e.g., Minikube, EKS, GKE, AKS, etc.)
- `kubectl` configured to interact with your cluster
- `helm` installed and configured
````
## Installation Steps

1. **Clone the Repository**

   First, clone the DevOps training repository which contains the necessary Helm chart configuration for Jenkins.

   ```bash
   git clone https://github.com/vivekkontham/DevOps_Training.git


2. **Navigate to the Jenkins Helm Chart Directory**

   Change your working directory to the Jenkins Helm chart location.

   ```bash
   cd DevOps_Training/Kubernetes/Installations/rootfiles/jenkins
   ```

3. **Install Jenkins Using Helm**

   Use the following command to install Jenkins into a new Kubernetes namespace called `jenkins`.

   ```bash
   helm install jenkins-kubernetes --namespace jenkins --create-namespace .
   ```

## Post Installation

* To check the status of the Jenkins installation:

  ```bash
  helm status jenkins-kubernetes -n jenkins
  ```

* To get the Jenkins admin password (if set by the chart values):

  ```bash
  kubectl exec -it <jenkins-pod-name> -n nexus -- cat /var/jenkins_home/secrets/initialAdminPassword

  ```

* To access the Jenkins UI:

   ```bash
   kubectl get svc -n jenkins
   ```

   Look for the `EXTERNAL-IP` of the `jenkins` service. Once it's available, open your browser and go to:

   ```
   http://<EXTERNAL-IP>:8080
   ```

   > 📌 Default Nexus UI Port: `8080`

## Cleanup

To uninstall Jenkins and delete the namespace:

```bash
helm uninstall jenkins-kubernetes -n jenkins
kubectl delete namespace jenkins
```

---

## Notes

* Ensure your Kubernetes cluster has sufficient resources for Jenkins.
* Customize values by editing the `values.yaml` file in the same directory before installing.

