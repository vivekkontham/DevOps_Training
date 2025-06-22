# Sonar Installation on Kubernetes

````markdown

## Prerequisites

- A running Kubernetes cluster (e.g., Minikube, EKS, GKE, AKS, etc.)
- `kubectl` configured to interact with your cluster
- `helm` installed and configured
````
## Installation Steps

1. **Clone the Repository**

   First, clone the DevOps training repository which contains the necessary configuration files for Sonarqube.

   ```bash
   git clone https://github.com/vivekkontham/DevOps_Training.git


2. **Navigate to the sonar manifest file Directory**

   Change your working directory to the sonarqube manifest files.

   ```bash
   cd DevOps_Training/Kubernetes/Installations/rootfiles/sonarqube/
   ```

3. **Installing Sonarqube**

   Use the following command to install Sonarqube into a new Kubernetes namespace called `Sonar`.

   ```bash
   kubectl create ns sonar && kubectl create -f sonar.yaml -n sonar
   ```

## Post Installation

* To check the status of the Sonarqube installation:

  ```bash
  kubectl get pods -n sonar
  ```


* To access the Sonarqube UI:

   ```bash
   kubectl get svc -n sonar
   ```

   Look for the `EXTERNAL-IP` of the `Sonarqube` service. Once it's available, open your browser and go to:

   ```
   http://<EXTERNAL-IP>:80
   ```

## Cleanup

To uninstall Sonarqube and delete the namespace:

```bash
kubectl delete -f sonar.yaml -n sonar
kubectl delete namespace sonar
```

---

## Notes

* Ensure your Kubernetes cluster has sufficient resources for sonar.
