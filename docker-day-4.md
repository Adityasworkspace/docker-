## 🛠️ Dockerfile - Day 4 Docker Learning

### 📦 What is a Dockerfile?

A Dockerfile contains a set of instructions to build a Docker image.

📁 **Filename**: `Dockerfile`

### 🧱 Common Keywords Used in Dockerfile:

* `FROM` — Specifies the base image
* `MAINTAINER` — Author of the Dockerfile
* `RUN` — Instructions to execute during image creation
* `CMD` — Instructions executed at container start
* `ENTRYPOINT` — Fixed instructions executed at container start
* `COPY` — Copy files from host to container
* `ADD` — Like `COPY` but also supports remote URLs and archive extraction
* `WORKDIR` — Sets the working directory inside the container
* `USER` — Specifies the user to run the container
* `EXPOSE` — Specifies which port the container listens on

### 🔹 Keyword Examples

**FROM**

```Dockerfile
FROM openjdk:17
FROM python:3.3
FROM node:19.5
FROM mysql:8.5
FROM tomcat:9.0
```

**MAINTAINER**

```Dockerfile
MAINTAINER Aditya <adityachikte168@gmail.com>
```

**RUN**

```Dockerfile
RUN git clone <url>
RUN mvn clean package
```

**CMD**

```Dockerfile
CMD java -jar app.jar
CMD python app.py
```

**ENTRYPOINT**

```Dockerfile
ENTRYPOINT ["java", "-jar", "app.jar"]
ENTRYPOINT ["python", "app.py"]
```

**COPY**

```Dockerfile
COPY target/app.jar /usr/app/app.jar
```

**ADD**

```Dockerfile
ADD target/app.jar /usr/app/app.jar
ADD http://example.com/app.jar /usr/app/app.jar
```

**WORKDIR**

```Dockerfile
WORKDIR /usr/app
```

**USER**

```Dockerfile
USER ec2-user
```

**EXPOSE**

```Dockerfile
EXPOSE 8080
```

---

## 🧪 Sample Dockerfile

```Dockerfile
FROM ubuntu

MAINTAINER Ashok <ashok.b@oracle.com>

RUN echo 'hello from run instruction-1'
RUN echo 'hello from run instruction-2'

CMD echo 'hi from cmd-1'
CMD echo 'hi from cmd-2'
```

---

### 🧱 Dockerfile Usage

```bash
# Build Docker image from Dockerfile
docker build -t img-1 .

# Run Docker container from the image
docker run img-1
```
