# Jenkins-Pipeline

This project describes how to set up a Jenkins pipeline on a virtual machine (VM) running in Oracle VirtualBox, with Docker agents to run builds inside containers. This setup allows you to automate your CI/CD process using Jenkins and Docker, with the pipeline code stored in a GitHub repository.

## Prerequisites

Before proceeding, ensure that you have the following:

- Oracle VirtualBox installed.
- A Linux-based OS (e.g., Ubuntu) installed on your VM.
- Basic knowledge of Docker and Jenkins.
- A GitHub repository containing your Jenkins pipeline code.

### Install Java and Jenkins

Once the VM is set up, you need to install Java and Jenkins.

#### Install Java
```bash
sudo apt update
sudo apt install openjdk-17-jre
java --version
```

#### Install Jenkins
```bash
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

#### Access Jenkins
```bash
http://<VM-IP>:8080
```

#### Install Docker and Grant permission
```bash
sudo apt update
sudo apt install docker.io
sudo usermod -aG docker jenkins
```

#### Restart Docker
```bash
http://<VM-IP>:8080/restart
```

### 6. Install Docker Pipeline Plugin

1. Log in to Jenkins.
2. Go to **Manage Jenkins > Manage Plugins**.
3. In the **Available** tab, search for **Docker Pipeline**.
4. Click **Install** to install the plugin.
5. After the plugin is installed, restart Jenkins to apply the changes.



### 7. Configure Jenkins Pipeline with Docker Agent

1. In Jenkins, create a new **Pipeline** job.
2. Under the **Pipeline** section, select **Pipeline script from SCM**.
3. Choose **Git** as the SCM option.
4. Provide the **GitHub repository URL** where your Jenkins pipeline code resides.
5. Jenkins will automatically fetch the pipeline code and execute it using Docker containers.


### 8. Set Up Jenkins Pipeline from GitHub Repository

Now pipeline job is configured and Jenkins ca be set to automatically fetch and execute the pipeline code stored in your GitHub repository.

