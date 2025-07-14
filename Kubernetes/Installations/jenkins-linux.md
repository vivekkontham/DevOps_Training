
````markdown
# 🚀 Jenkins Installation on Debian/Ubuntu

````
---

## Prerequisites

- A system running **Debian or Ubuntu**
- `sudo` privileges
- Internet access

---

## Step 1: Update System Packages

```bash
sudo apt update
sudo apt upgrade -y
```

---

## Step 2: Install Java (Default JRE)

Jenkins requires Java to run. Install the default Java Runtime Environment (usually OpenJDK 11 or higher):

```bash
sudo apt install -y fontconfig default-jre
```

>  You can verify installation using:

```bash
java -version
```

---

## Step 3: Add Jenkins Repository

Import the Jenkins repository and GPG key:

```bash
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```

---

## Step 4: Install Jenkins and Dependencies

Update your system’s APT index and install Jenkins with required dependencies:

```bash
sudo apt-get update
sudo apt-get install -y jenkins
```

---

## 🔧 Step 5: Start and Enable Jenkins

```bash
sudo systemctl enable jenkins
sudo systemctl start jenkins
```

---

## 🩺 Step 6: Check Jenkins Status

```bash
sudo systemctl status jenkins
```

---

## 🌐 Step 7: Access Jenkins Web Interface

Open your browser and go to:

```
http://<your-server-ip>:8080
```

To get the initial admin password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy this password and paste it into the Jenkins UI to unlock the setup wizard.

---

## 📌 Notes

* Jenkins runs on **port 8080** by default.
* You may need to allow port 8080 in your firewall:

  ```bash
  sudo ufw allow 8080
  ```

---

## 🧹 Uninstallation (if needed)

```bash
sudo apt remove --purge jenkins
sudo apt autoremove
```

---

## 📚 References

* [Jenkins Official Documentation](https://www.jenkins.io/doc/)
* [Jenkins Debian Package Repo](https://pkg.jenkins.io/debian-stable/)


---
