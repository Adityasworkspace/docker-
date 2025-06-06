# ![Docker Logo](https://www.docker.com/wp-content/uploads/2022/03/vertical-logo-monochromatic.png)

# 🐳 Docker for Application Deployment

---

## 📦 Application Architecture

1. **Frontend** – User Interface (UI)
2. **Backend** – Business Logic
3. **Database** – Storage

---

## 💻 Tech Stack of Application

| Layer     | Technology       |
| --------- | ---------------- |
| Frontend  | Angular 16       |
| Backend   | Java 17          |
| Database  | MySQL Server 8.5 |
| Webserver | Tomcat 9.0       |

> 💡 **Note:** To run our application code, we need to set up all required **dependencies** in the machine.

**Dependencies** are the software tools/services necessary to run the app:

* Java
* Angular
* MySQL
* Tomcat

---

## 🌐 Application Environments

In real-time, we use multiple environments to test and validate the application:

| Environment | Purpose                      |
| ----------- | ---------------------------- |
| DEV         | Code Integration Testing     |
| SIT         | System Integration Testing   |
| UAT         | Client Acceptance Testing    |
| PILOT       | Pre-Production Testing       |
| PROD        | Final Delivery for End Users |

> ✅ As a **DevOps Engineer**, you're responsible for setting up the infrastructure to run the application.

* Install all required software/dependencies
* Ensure the environment is consistent across all stages

**Challenges:**

* Manual dependency installations are prone to errors
* Version mismatches can break applications

---

## 🐳 Why Docker?

Docker simplifies application execution by:

* Packaging all dependencies into containers
* Ensuring environment consistency
* Avoiding manual setup errors
* Making the app portable and scalable

With Docker, you can:

* Create isolated environments for every component (Frontend, Backend, DB)
* Use Dockerfiles and docker-compose to automate setup
* Deploy consistently across DEV, UAT, PROD environments

---

