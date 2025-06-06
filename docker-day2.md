# 🐳 Docker for Application Deployment

---

## 📘 What is Docker?

* Docker is a **free & open-source software**
* It is used for **containerization**
* Docker helps run applications on **any machine** without worrying about environment setup

> **Container** = App Code + Dependencies (packaged together)

* Docker handles the dependencies needed for running applications
* It ensures application **portability** and **consistency** across environments

---

## 📦 Docker Architecture

![Docker Architecture](https://media.geeksforgeeks.org/wp-content/uploads/20221205115118/Architecture-of-Docker.png)

1. **Dockerfile** – Specifies app code location and required dependencies

   > Used to **build Docker images**

2. **Docker Image** – A packaged snapshot of code + dependencies

3. **Docker Registry** – A centralized location to store Docker images (e.g., Docker Hub)

4. **Docker Container** – A running instance of a Docker image (isolated lightweight Linux environment)

> Running a Docker image creates a container where the app executes.

---

## 🛠️ Install Docker on Linux VM

Follow these steps to install Docker on an Amazon Linux EC2 instance:

### 🔹 Step 1: Create an EC2 Instance

* Use Amazon Linux
* Connect via SSH to the instance

### 🔹 Step 2: Install Docker

```bash
sudo yum update -y
sudo yum install docker -y
sudo service docker start
```

### 🔹 Step 3: Add User to Docker Group

```bash
sudo usermod -aG docker ec2-user
```

### 🔹 Step 4: Reconnect

* Exit the terminal and reconnect to apply group changes

```bash
exit
```

### 🔹 Step 5: Verify Docker Installation

```bash
docker -v
```

> ✅ Now Docker is installed and ready to use on your Linux VM

---

## 📂 Upload This to GitHub

Save this content as `README.md` and push it to your DevOps learning repository for **Docker Basics** 🚀
