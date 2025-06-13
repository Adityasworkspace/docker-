# Day 7: Docker 

---

## 🐳 Accessing Docker Container

# Display running Docker containers
```bash
$ docker ps
```
# Get into container using container ID
```bash
$ docker exec -it <container-id> /bin/bash
```

# Check files in current directory
```bash
$ ls -l
```

# Exit from container back to host
```bash
$ exit
```

---
### 🌱 Spring Boot with MySQL DB using Docker Compose
```bash
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
      - /data/mysql

networks:
  springboot-db-net:
```

---

## ⚙️ Application Execution Process

# Clone git repo
```bash
$ git clone https://github.com/ashokitschool/spring-boot-mysql-docker-compose.git
```
# Go inside project directory
```bash
$ cd spring-boot-mysql-docker-compose
```

# Build project using Maven
```bash
$ mvn clean package
```

# Build Docker image
```bash
$ docker build -t spring-boot-mysql-app .
```

# Check Docker images
```bash
$ docker images
```

# Create Docker containers using Docker Compose
```bash
$ docker-compose up -d
```
# Check running containers
```bash
$ docker-compose ps
```
# Stop running containers
```bash
$ docker-compose stop
```
# Start containers again
```bash
$ docker-compose start
```
# Remove containers, networks, volumes
```bash
$ docker-compose down
```

### 🌐 Docker Network Basics
```bash
Docker network enables communication between containers.

Containers on the same network can talk to each other.

🔸 Default Docker Networks
bridge – Assigns IP to container (default)

host – No separate IP; shares host network

none – No network

🔸 Additional Networks
overlay – Used for Docker Swarm orchestration

macvlan – Assigns physical IP to container


# Display Docker networks
```bash
$ docker network ls
```

# Create Docker network
```bash
$ docker network create ashokit-nw
```

# Inspect Docker network
```bash
$ docker network inspect ashokit-nw
```
# Create container with custom network
```bash
$ docker run -d -p 8080:8080 --network ashokit-nw sb-app-image
```
# Remove Docker network
```bash
$ docker network rm ashokit-nw
```


🧱 Docker Compose Overview
```
Previously, apps were monolithic (everything in one app).

Now, most projects use Microservices Architecture:

Ex: hotels-api, flights-api, trains-api, cabs-api

Each microservice runs in its own container.

Managing many containers manually is hard.

💡 Solution: Docker Compose

Manages multi-container apps.

One command to start/stop all services.
```

📄 What is docker-compose.yml?
```
Configuration file for Docker Compose.

Default name is docker-compose.yml.

🔹 Contains 4 Sections:
version – Compose file version

services – Containers' configuration

networks – Define custom networks

volumes – Define persistent storage

🔧 Docker Compose Setup
```

# Install Docker Compose
```bash
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
# Make it executable
```bash
$ sudo chmod +x /usr/local/bin/docker-compose
```
# Verify installation
```bash
$ docker-compose --version
```
---









