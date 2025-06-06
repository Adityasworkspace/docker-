As a in wonderful day 03 we learned DOCKER COMMANDS
## 🧰 Common Docker Commands

| Command                       | Description                                      |
| ----------------------------- | ------------------------------------------------ |
| `docker images`               | List all available Docker images                 |
| `docker ps`                   | Show running Docker containers                   |
| `docker ps -a`                | Show all (running + stopped) containers          |
| `docker logs <container-id>`  | Display logs of a container                      |
| `docker pull <image-name>`    | Download Docker image from Docker Hub            |
| `docker rmi <image-id/name>`  | Delete Docker image                              |
| `docker run <image-name>`     | Create and run a Docker container                |
| `docker stop <container-id>`  | Stop a running container                         |
| `docker start <container-id>` | Start a stopped container                        |
| `docker rm <container-id>`    | Remove a container                               |
| `docker system prune -a`      | Delete stopped containers, unused images & cache |

---

## 🚀 Running Real-World Applications Using Docker Images

### 🔸 Spring Boot REST API

```bash
docker pull ashokit/spring-boot-rest-api
docker run -d ashokit/spring-boot-rest-api
docker run -d -p 9090:9090 ashokit/spring-boot-rest-api
```

URL:

```
http://<public-ip>:9090/welcome/{name}
```

### 🔸 Python Flask Application

```bash
docker pull ashokit/python-flask-app
docker run -d ashokit/python-flask-app
docker run -d -p 5000:5000 ashokit/python-flask-app
```

URL:

```
http://<public-ip>:5000/
```

> ✅ `-d` = detached mode (run in background)
> 
> ✅ `-p` = port mapping (host-port\:container-port)
> 
> ✅ Make sure the host port is allowed in EC2 security group inbound rules
