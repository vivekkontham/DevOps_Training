
````markdown
# 🚀 Argo CD Installation Guide

This guide provides step-by-step instructions to install **Argo CD** on a Kubernetes cluster, expose its UI via a LoadBalancer service, install the Argo CD CLI, and retrieve the initial admin password.
````
---

## 📋 Prerequisites

Before you begin, ensure the following tools are installed and configured:

- A **running Kubernetes cluster**
- `kubectl` configured to access the cluster
- Internet access to fetch manifests and binaries
- `curl`, `sed`, and `grep` (common on Unix-like systems)

---

## 🧩 Step 1: Create Argo CD Namespace

Create a dedicated namespace for Argo CD resources:

```bash
kubectl create namespace argocd
```

---

## 📦 Step 2: Install Argo CD Components

Apply the official Argo CD installation manifest to deploy its components in the `argocd` namespace:

```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

This will create Argo CD components including the API server, controller, repo server, and UI.

---

## 🌐 Step 3: Expose the Argo CD API Server

Patch the `argocd-server` Kubernetes service to make it accessible via an external IP:

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```

Wait a few moments, then check for the external IP address:

```bash
kubectl get svc argocd-server -n argocd
```

Copy the EXTERNAL-IP from the output and use it to access the Argo CD UI in your browser.

---

## 💻 Step 4: Install Argo CD CLI

To interact with Argo CD from your terminal, download and install the latest version of the Argo CD CLI:

```bash
VERSION=$(curl --silent "https://api.github.com/repos/argoproj/argo-cd/releases/latest" | grep '"tag_name"' | sed -E 's/.*"([^"]+)".*/\1/')
curl -sSL -o argocd "https://github.com/argoproj/argo-cd/releases/download/${VERSION}/argocd-linux-amd64"
chmod +x argocd
sudo mv argocd /usr/local/bin/
```

> 📌 Adjust the download URL for your operating system if you're not using Linux. For example, use `argocd-darwin-amd64` for macOS.

Verify the installation:

```bash
argocd version
```

---

## 🔑 Step 5: Retrieve the Initial Admin Password

The default Argo CD admin password is stored as a Kubernetes secret. Retrieve it using the following command:

```bash
argocd admin initial-password -n argocd
```

Alternatively, you can also use:

```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d && echo
```

---

## 🔐 Step 6: Log In to Argo CD

### Option A: Web UI

1. Navigate to the Argo CD UI in your browser using the LoadBalancer external IP:

   ```
   https://<ARGOCD_EXTERNAL_IP>
   ```

2. Login with:

   * **Username:** `admin`
   * **Password:** (from Step 5)

> ⚠️ If using a self-signed certificate, your browser may show a security warning. Proceed to continue.

### Option B: CLI Login

Use the Argo CD CLI to log in:

```bash
argocd login <ARGOCD_EXTERNAL_IP> --username admin --password <PASSWORD> --insecure
```

Use `--insecure` to skip TLS verification if Argo CD is using a self-signed certificate.

---

## 📚 Additional Resources

* [Argo CD Official Documentation](https://argo-cd.readthedocs.io/)
* [Argo CD GitHub Repository](https://github.com/argoproj/argo-cd)
* [Argo CD CLI Commands](https://argo-cd.readthedocs.io/en/stable/cli_reference/argocd/)

---

## ✅ Summary

| Step | Description                         |
| ---- | ----------------------------------- |
| 1    | Create `argocd` namespace           |
| 2    | Install Argo CD components          |
| 3    | Expose the UI via LoadBalancer      |
| 4    | Install the Argo CD CLI             |
| 5    | Retrieve the initial admin password |
| 6    | Access Argo CD via UI or CLI        |

You're now ready to deploy and manage applications with Argo CD!

---
