# 🐳 Day 6: Docker – Dockerizing a Java Web Application & Pushing to Docker Hub

---

## ✅ Building and Running Docker Image

### 🔹 Step 1: Create Docker Image Using Dockerfile

```bash
$ docker build -t img-1 .
```

### 🔹 Step 2: Run Docker Image to Create Docker Container

```bash
$ docker run img-1
```

---

## ☁️ Pushing Docker Image to Docker Hub

### 🔹 Step 1: Login to Docker Hub

```bash
$ docker login
```

### 🔹 Step 2: Tag the Docker Image

```bash
$ docker tag <image-name> <dockerhub-username>/<image-name>
```

**Example:**

```bash
$ docker tag img-1 ashokit/img-1
```

### 🔹 Step 3: Push the Docker Image

```bash
$ docker push <dockerhub-username>/<image-name>
```

---

## 🧩 Dockerizing a Java Web Application

### 📌 Key Points

- Java web app will be packaged as a `.war` file.
- The `.war` file is generated inside the `target/` directory.
- To deploy it, a web server like **Tomcat** is used.
- Place the `.war` file in `webapps/` directory of Tomcat to run the application.

---

## 📦 Dockerfile to Run Java Web App

```dockerfile
FROM tomcat:latest

MAINTAINER Ashok

EXPOSE 8080

COPY target/app.war /usr/local/tomcat/webapps/
```

---

## 🔗 Java Web App Git Repository

[Java Web App GitHub Repo](https://github.com/ashokitschool/maven-web-app.git)

---

## 🛠️ Steps to Build and Run the App

```bash
# Install dependencies
$ sudo yum install git
$ sudo yum install maven

# Clone the repo
$ git clone https://github.com/ashokitschool/maven-web-app.git

# Navigate into the project
$ cd maven-web-app

# Package the application
$ mvn clean package

# Verify WAR file is generated
$ ls -l target/

# Build Docker image
$ docker build -t <img-name> .

# Check Docker images
$ docker images

# Run the container
$ docker run -d -p <host-port>:8080 <img-name>
```

---

## 🌐 Accessing the Application

> Make sure the host port is open in the **Security Group → Inbound Rules** (if using a cloud provider like AWS).

📌 **URL:**  
```
http://<public-ip>:<host-port>/<war-file-name>/
```
