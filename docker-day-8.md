
---


# ⚖️ Stateful vs Stateless Containers



## Stateless Container
```bash
- Data is **deleted** after container is removed.
- Docker containers are **stateless by default**.
```
## Stateful Container
```bash
- Data is **persisted permanently**, even after container removal.
```

📝 **Example**:  
In a Spring Boot + MySQL setup, the MySQL database runs inside a Docker container.  
When containers are recreated, the DB is also reset — **data is lost**, which is not acceptable in real-time environments.

➡️ To solve this, we make containers **stateful** using **Docker Volumes**.
```



## 🗃️ Docker Volumes
```bash
- Volumes persist data generated by Docker containers.
- Prevent data loss.
- Help in creating **stateful containers**.
```

## 🔹 Types of Docker Volumes
```bash
1. Anonymous Volume (no name)
2. Named Volume
3. Bind Mounts
```
### 📦 Volume Commands


# List Docker volumes
```bash
$ docker volume ls
```
# Create a Docker volume
```bash
$ docker volume create <vol-name>
```
# Inspect a Docker volume
```bash
$ docker volume inspect <vol-name>
```
# Remove a specific Docker volume
```bash
$ docker volume rm <vol-name>
```
# Remove all unused volumes
```bash
$ docker system prune --volumes
````

---

# 🛠️ Making Docker Containers Stateful

### ✅ Steps

1. Create a mount directory on host (e.g., `/home/ec2-user/`):

```bash
$ mkdir app
```

2. Modify `docker-compose.yml` to mount volume:

```yaml
version: "3"
services:
  application:
    image: spring-boot-mysql-app
    ports:
      - "8080:8080"
    networks:
      - springboot-db-net
    depends_on:
      - mysqldb
    volumes:
      - /data/springboot-app

  mysqldb:
    image: mysql:5.7
    networks:
      - springboot-db-net
    environment:
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_DATABASE=sbms
    volumes:
      - ./app:/var/lib/mysql

networks:
  springboot-db-net:
```

---

# 🐝 Docker Swarm

## ⚙️ What is Docker Swarm?

* Docker Swarm is an **orchestration tool**.
* Orchestration = Managing containers across **multiple servers (cluster)**.
* A **Swarm Cluster** is a group of Docker nodes (servers).

---

# 🏗️ Swarm Cluster Setup

### 🔧 Prerequisites

* Create **3 EC2 Ubuntu instances**.
* Install Docker:

```bash
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
```

✅ **Enable port 2377** in EC2 security group.

### 📌 Cluster Roles

* 1 Master Node
* 2 Worker Nodes

### 🚀 Initialize Swarm on Master Node

```bash
$ sudo docker swarm init --advertise-addr <private-ip-of-master-node>
```

🔁 Example:

```bash
$ sudo docker swarm init --advertise-addr 172.31.41.217
```

### 🔐 Get Join Token for Worker Nodes

```bash
$ sudo docker swarm join-token worker
```

* Copy the token and run it on each worker node:

```bash
$ sudo docker swarm join --token <token> <master-private-ip>:2377
```

---

# 🧰 Docker Swarm Services

* A **Service** is a logical collection of containers.
* Docker Swarm supports:

  1. Replica (default)
  2. Global

### ➕ Create a Service

```bash
$ sudo docker service create --name <serviceName> -p <hostPort>:<containerPort> <imageName>
```

🔁 Example:

```bash
$ sudo docker service create --name java-web-app -p 8080:8080 ashokit/javawebapp
```

🧭 Access app at:

```
http://<master-node-public-ip>:8080/java-web-app/
```

---

## 🔍 Service Commands


# List services
```bash
$ sudo docker service ls
```
# Scale a service
```bash
$ docker service scale <serviceName>=<replica-count>
```
# Inspect a service
```bash
$ sudo docker service inspect --pretty <service-name>
```
# View service task status
```bash
$ sudo docker service ps <service-name>
```
# Remove node from swarm
```bash
$ sudo docker swarm leave
```
# Remove a service
```bash
$ sudo docker service rm <service-name>
```





##So that's it for DOCKER

