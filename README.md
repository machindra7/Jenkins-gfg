# 🚀 Welcome to the DevOps Test Repository (Maven Project) #

This repository is created for **DevOps practice using a Maven-based Java application**.
It covers **Maven setup, build process, Docker image creation, and container execution** in a very simple and beginner-friendly way.

---

## 📌 Objective

* Install Java and Maven
* Build a Java application using Maven
* Generate a WAR file
* Create a Docker image
* Run the application inside a Docker container
* Access the application from a browser

---

## 🧰 Prerequisites

* Ubuntu-based Linux system
* sudo access
* Internet connectivity
* Jenkins already installed (port 8080 is occupied)

---

## ☕ Step 1: Install Java (Required for Maven)

Install OpenJDK 17:

```bash
sudo apt install openjdk-17-jdk -y
```

Verify Java installation:

```bash
java -version
```

---

## 📦 Step 2: Install Latest Maven Version (Manual Installation)

> ⚠️ We are installing **latest Maven manually** instead of using `apt install maven`

```bash
cd /opt
sudo wget https://dlcdn.apache.org/maven/maven-3/3.9.11/binaries/apache-maven-3.9.11-bin.tar.gz
sudo tar -xvzf apache-maven-3.9.11-bin.tar.gz
sudo ln -s /opt/apache-maven-3.9.11 /opt/maven
sudo ln -s /opt/maven/bin/mvn /usr/bin/mvn
sudo apt install maven -y
```
Verify Maven installation:

```bash
mvn --version
```

---

## 🔐 Step 3: Jenkins Permission Changes (If Required)

Check Jenkins status:

```bash
systemctl status jenkins
```

Edit Jenkins service file:

```bash
vi /usr/lib/systemd/system/jenkins.service
```

Reload and restart Jenkins:

```bash
systemctl daemon-reload
systemctl restart jenkins
```

---

## 🧹 Step 4: Clean Previous Builds Using Maven

Navigate to the project directory and run:

```bash
mvn clean
```

---

## 📦 Step 5: Package the Application (WAR File)

```bash
mvn package
```

After successful build:

* Go to the `target/` directory
* Verify the WAR file named:

```
devops.war
```

---

## 🐳 Step 6: Build Docker Image

Make sure the `Dockerfile` is present in the project directory.

Build the Docker image:

```bash
docker build -t image-name:version .
```

Example:

```bash
docker build -t devops-app:1.0 .
```

---

## 🧹 Step 7: Remove Existing Containers (Optional Cleanup)

```bash
docker rm -f `docker ps -aq`
```

---

## ▶️ Step 8: Run Docker Container

> ⚠️ Port **8080 is already used by Jenkins**, so we use **8081**

```bash
docker run -d -p 8081:8080 --name mynewcontainer image-name:version
```

Example:

```bash
docker run -d -p 8081:8080 --name mynewcontainer devops-app:1.0
```

---

## 🌐 Step 9: Access the Application

Open your browser and use:

```
http://<SYSTEM-IP>:8081/devops
```

Example:

```
http://192.168.1.10:8081/devops
```

---

## ✅ Lab Completed 🎉

You have successfully:

* Installed Java and Maven
* Built a Maven project
* Created a WAR file
* Dockerized the application
* Deployed and accessed it via browser

---

⭐ **Happy Learning & Keep Practicing DevOps!**
