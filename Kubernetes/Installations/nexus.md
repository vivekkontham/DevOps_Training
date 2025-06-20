# Nexus Repository Manager Installation on Kubernetes

````markdown
## ✅ Prerequisites

Ensure the following tools are installed and properly configured:

- `kubectl` (Kubernetes CLI)
- `helm` (Helm package manager)
- `gke-gcloud-auth-plugin` (Only if you're using Google Kubernetes Engine)

````
## 🚀 Installation Steps

1. **Add the Sonatype Helm Repository**
   ```bash
   helm repo add sonatype https://sonatype.github.io/helm3-charts/

2. **Update the Helm Repositories**

   ```bash
   helm repo update
   ```

3. **Create a Namespace for Nexus**

   ```bash
   kubectl create ns nexus
   ```

4. **Install Nexus Using Helm**

   ```bash
   helm install nexus sonatype/nexus-repository-manager --namespace nexus
   ```

5. **Expose Nexus via LoadBalancer**
   Edit the Nexus service to change the type to `LoadBalancer`:

   ```bash
   kubectl edit svc nexus-nexus-repository-manager -n nexus
   ```

   In the opened editor, find the line:

   ```yaml
   type: ClusterIP
   ```

   and change it to:

   ```yaml
   type: LoadBalancer
   ```

6. **Access Nexus Web UI**
   After changing the service type, wait for an external IP to be assigned:

   ```bash
   kubectl get svc -n nexus
   ```

   Look for the `EXTERNAL-IP` of the `nexus-nexus-repository-manager` service. Once it's available, open your browser and go to:

   ```
   http://<EXTERNAL-IP>:8081
   ```

   > 📌 Default Nexus UI Port: `8081`

---

## 📝 Notes

* It may take a couple of minutes for the external IP to be provisioned.
* Default credentials (unless changed in the Helm chart values):

  * **Username:** `admin`
  * **Password:** You can find the initial password by running:

    ```bash
    kubectl exec -it <nexus-pod-name> -n nexus -- cat /nexus-data/admin.password
    ```

---

## 📚 References

* [Sonatype Helm Charts](https://sonatype.github.io/helm3-charts/)
* [Nexus Repository Manager Docs](https://help.sonatype.com/repomanager3)

