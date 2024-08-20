# docker-learning from Ashok It

# Docker Notes

## Table of Contents

1. [What is an Application?](#what-is-an-application)
2. [Application Tech Stack](#application-tech-stack)
3. [Application Architecture](#application-architecture)
4. [Life without Docker](#life-without-docker)
5. [Life with Docker](#life-with-docker)
6. [What is Docker?](#what-is-docker)
7. [What is Virtualization?](#what-is-virtualization)
8. [What is Containerization?](#what-is-containerization)
9. [Docker Architecture](#docker-architecture)
10. [Application Environments](#application-environments)

## What is an Application?

An application is nothing but a collection of programs.

## Application Tech Stack

Every application contains 3 layers:

1. **Frontend (UI)**

   - Angular
   - React JS
   - Vue JS

2. **Backend (Business Logic)**

   - Java
   - .Net
   - Python
   - Node JS
   - PHP

3. **Database**
   - Oracle
   - MySQL
   - Postgres
   - SQL Server
   - MongoDB

## Application Architecture

Applications are typically structured into three main layers: frontend, backend, and database. Each layer is responsible for different aspects of the application.

## Life without Docker

- We need to install all the required software in all environments to run our application.
- We must ensure we are using the same versions of software across all machines.
- If any software version does not match, application execution may fail.

  Example:

  - Raja installed Java 11 in the Dev Environment.
  - Sunil installed Java 8 in the SIT Environment.

- If we want to run our application on multiple machines, we have to install the required software on all those machines, which is a hectic task.

## Life with Docker

## What is Docker?

## What is Virtualization?

## What is Containerization?

## Docker Architecture

## Application Environments

In real-time, our application will be deployed into multiple environments for testing purposes:

1. **DEV Environment** - Developers Testing
2. **SIT Environment** - Testing Team (QA) - System Integration
3. **UAT Environment** - Client-Side Testing - User Acceptance Testing
4. **PILOT Environment (Pre-Production)** - Testing with Live Data

Once testing is completed in all the above environments, it will be deployed into the **PRODUCTION Environment**.

- **Production Environment** means a live environment.
- End users will access the application from the Production Environment.

## Life with Docker

- Docker is a containerization platform.
- Docker is used to build and deploy our application into any machine without worrying about dependencies.
- Dependencies are the software components required to run our application.

  Examples of Dependencies:

  - Operating System (OS)
  - Angular
  - React
  - Java
  - Database (DB)
  - Tomcat

- Docker reduces the gap between Development and Deployment.

  ![image](https://github.com/user-attachments/assets/3285a72f-5a83-42b5-b089-37c00ebf59c0)


## Docker Architecture

1. **Dockerfile**:

   - A text file containing instructions to build a Docker image.

2. **Docker Image**:

   - A lightweight, stand-alone, and executable package that includes everything needed to run a piece of software, including the code and the dependencies.

3. **Docker Registry**:

   - A repository to store Docker images. Examples include Docker Hub and private registries.

4. **Docker Container**:
   - A runtime instance of a Docker image. It runs our application in an isolated environment.

**Note**: Once a Docker image is created, it can be pulled and run on any machine, ensuring consistency across development, testing, and production environments.

## Virtualization

- Virtualization involves installing multiple Guest Operating Systems (OS) on a single Host Operating System.
- A **Hypervisor** software is used to achieve virtualization.
- All required software must be installed on each Guest OS to run an application.
- This is an older technique used to run applications.
- System performance may degrade due to the overhead of running multiple OS instances.
- **Containerization** is a modern approach that overcomes the limitations of virtualization.

## Containerization

- Containerization packages all required software and application code into a single container for execution.
- The container handles everything needed to run the application.
- Containers can easily be run on multiple machines.
- **Docker** is a popular containerization software.
  - Using Docker, we can create containers for our applications.
  - Docker allows us to create images for our applications.
- Docker images can be easily shared across multiple machines.
- Docker containers can be created from Docker images and executed efficiently.

## Conclusion

- Docker is a containerization software that simplifies application deployment and management.
- Docker manages both the application and its dependencies, ensuring consistent execution across environments.
- Using Docker containers, application deployments to multiple environments become easier and more reliable.

================================================================

🔥 **Launching EC2 Instance in AWS**: [Watch Tutorial](https://youtu.be/uI2iDk8iTps)

🔥 **Connect to EC2 using Putty**: [Watch Tutorial](https://youtu.be/GXc_bxmP0AA)

================================================================

## Environment Setup

1. **Create an Account in AWS Cloud**
2. **Create a Linux Machine using AWS EC2 Service**
   - Image: Amazon Linux
3. **Connect to Linux Machine using MobaXterm or Putty**
4. **Install Docker Software in Linux VM** using the following commands:

### Install Docker in Amazon Linux

```bash
# Update the package database
$ sudo yum update -y

# Install Docker
$ sudo yum install docker -y

# Start Docker service
$ sudo service docker start

# Add ec2-user to the docker group to manage Docker as a non-root user
$ sudo usermod -aG docker ec2-user

# Exit the session to apply group changes
$ exit

# Reconnect and verify Docker installation
$ docker info
```

# Docker Commands

## Basic Docker Information

- **See Docker information:**

  ```bash
  docker info

  ```

- **List Docker images:**

  ```bash
  docker images

  ```

- **Pull the hello-world Docker image:**

  ```bash
  docker pull hello-world

  ```

- **Run the hello-world Docker image:**

  ```bash
  docker run hello-world

  ```

- **Display running Docker containers:**

  ```bash
  docker ps

  ```

- **Display running and stopped containers:**

  ```bash
  docker ps -a

  ```

- **Inspect a Docker image:**

  ```bash
  docker inspect <image-id>

  ```

- **Remove a Docker image:**

  ```bash
  docker rmi <image-name / image-id>

  ```

- **Forcefully remove a Docker image:**

  ```bash
  docker rmi -f <image-name / image-id>

  ```

- **Stop a running container:**

  ```bash
  docker stop <container-id>

  ```

- **Remove a Docker container:**

  ```bash
  docker rm <container-id>

  ```

- **Remove all stopped containers, unused images, and unused networks:**

  ```bash
  docker system prune -a
  ```

#### TO GET STATUS

## Overview

- **Dockerfile** contains a set of instructions to build a Docker image.
- It uses a Domain Specific Language (DSL).
- Docker Engine processes Dockerfile instructions from top to bottom.

## Key Dockerfile Keywords

1. **FROM**
2. **MAINTAINER**
3. **COPY**
4. **ADD**
5. **RUN**
6. **CMD**
7. **ENTRYPOINT**
8. **ENV**
9. **ARG**
10. **WORKDIR**
11. **EXPOSE**
12. **VOLUME**
13. **USER**
14. **LABEL**

---

### FROM

- Specifies the base image to create the Docker image.

**Syntax:**

```dockerfile
FROM java:1.8
FROM python:1.2
FROM mysql:8.5
FROM tomcat:9.5
```

# Dockerfile Instructions

## Maintainer

It is used to specify the Dockerfile author information.

**Syntax:**

```dockerfile
MAINTAINER Ashok <ashok.b@oracle.com>
```

# COPY Command in Docker

## Copy

The `COPY` command is used to copy files from the source to the destination while creating a Docker image.

**Syntax:**

```Dockerfile
COPY target/sb-api.war /app/tomcat/webapps/sb-api.war
```

## ADD

#### IT is used to copy the files from source to destination while creating docker image

**Syntax**:

```bash
ADD  <SRC>  <DESTINATION>
```

```bash
ADD  <HTTP-URL>  <DESTINATION>
```

```bash
Ex:    ADD  <url>   /app/tomcat/webapps/sb-api.war
```

### Q) What is the difference between COPY and ADD command?

- **COPY**: It can copy files from one path to another path within the same machine.

- **ADD**: It can copy files from one path to another path, and it also supports URLs as a source.

# RUN Command in Docker

The `RUN` instruction is used to execute commands while creating a Docker image.

## Syntax:

```Dockerfile
RUN yum install git
RUN yum install maven
RUN git clone <repo-url>
RUN cd <repo-name>
RUN mvn clean package
```

# CMD Command in Docker

- The `CMD` instruction is used to execute commands while creating a Docker container.
- Using the `CMD` command, you can run your application in the container.

## Syntax:

```Dockerfile
CMD sudo start tomcat

CMD java -jar <jar-file>
```

### Q) What is the difference between RUN and CMD?

- **RUN**: Instructions will execute while creating the Docker image.
- **CMD**: Instructions will execute while creating the Docker container.

- We can write multiple `RUN` instructions, docker engine will process from top to bottom.
- We can write multiple `CMD` instructions but docker engine will process only last CMD instruction.

**Note:** There is no use of writing multiple `CMD` instructions.

# Docker file Sample

```
FROM ubuntu

MAINTAINER Ashok<ashok.b@oracle.com>

RUN echo "Hi, i am run - 1"
RUN echo "Hi, i am run - 2"
RUN echo "Hi, i am run - 3"

CMD echo "Hi, i am CMD-1"
CMD echo "Hi, i am CMD-2"
CMD echo "Hi, i am CMD-3"
```

### Create a file (filename: Dockerfile)

```
$ vi Dockerfile
```

### Copy above sample docker file content and keep in docker

```
file  (Esc + :wq)
```

#### Create docker image using Dockerfile

```
$ docker build -t <image-name> .
```

## login into docker hub account from docker machine

```bash
$ docker login

Note: Enter your docker hub account credentials.
```

### Tag docker image

```bash
$ docker tag <image-name> <tagname>

Ex :  $ docker tag myimg1 ashokit/myimg1

```

### Push Docker image

```bash
$ docker push <Tag-name>
```

### Q) Can we use user defined name for Dockerfile ?

- ** Yes, we can do it. **.

```bash
$ docker build -f <filename> -t <imagename> .
```

# ENTRYPOINT

- **ENTRYPOINT**: It is used to execute instructions while creating container

**Synatx:**

```bash
ENTRYPOINT [ "echo" , "Container Created Successfully" ]

ENTRYPOINT [ "java", "-jar", "target/springboot.jar" ]
```

### Q) What is the difference between CMD and ENTRYPOINT ?

- **CMD**: CMD instructions we can override while creating container.

- **ENTRYPOINT**: ENTRYPOINT instructions we can't override.

**Note:** There is no use of writing multiple `CMD` instructions.

# WORKDIR

- **WORKDIR**: It is used to specify working directory for image and container.

**Synatx:**

```bash
  WORKDIR /app/usr/
```

# ENV

- **ENV**: ENV is used to set Environment Variables.

**Synatx:**

```bash
   Ex:

ENV java /etc/softwares/jdk
```

# EXPOSE

- **EXPOSE**: It is used to specify on which port number our docker container wil run

**Synatx:**

```bash
   EXPOSE 8080
```

# ARG

- **ARG**: IBy using ARG we can take dynamic values from CLI
- It is used to remove hard coded values in Dockerfile

**Synatx:**

```bash
   ARG branch
```

```bash
  RUN git clone -b $branch <repo-url>
```

```bash
$ docker build -t <imagename> --build-arg branch=master .
```

# USER

- **User**: It is used to specify username for creating image / container

**Synatx:**

```bash
  USER dockeruser
```

# VOLUME

- **VOLUME**: It is used to specify docker volume storage location
- Volumes are used for storage purpose

**Synatx:**

```bash

```

# LABEL

- **LABEL**: It is used to add METADATA to docker objects in key-value format

**Synatx:**

```bash
    LABEL name="sbi_image"
```

## 1) What is an application ?

## 2) Application Tech stack ?

## 3) Application Architecture

## 4) Life without Docker

## 5) Life with Docker

## 6) What is Docker

## 7) What is Virtualization ?

## 8) What is Containerization ?

## 9) Docker Architecture ?

## 10) Docker Installation in Linux

## 11) Docker Image Creation

## 12) Docker Container Creation

## 13) Dockerfile creation

## 14) Docker Registry (push image to registry)

## 15) Dockerfile Keywords

# Java Applications Dockerization

### We can see two types of Java applications in companies:

1. **Normal Java Application without Spring Boot**

2. **Java Application with Spring Boot**

_Note: Spring Boot is ready made framework to make java application development simple._

### Differences in Packaging and Deployment:

- **Normal Java Web Applications**  
   Normal Java Web Applications will be packaged as war file and war file will be deployed in webserver
  (Ex: tomcat)

- **Spring Boot Applications**  
  Spring Boot applications will be packaged as `jar` file and we need to run the jar file. It will take care of server internally (Embedded Server).

#### Java Maven Web App Git Repo : https://github.com/ashokitschool/maven-web-app.git

# Dockerfile For Java Web Application

```bash
FROM tomcat:8.0.20-jre8

COPY target/app.war  /usr/local/tomcat/webapps/app.war

EXPOSE 8080
```
















# Summary of Topics

## 1) What is Application Stack

An application stack refers to a collection of technologies and software products that are used together to create a web or mobile application. This typically includes the operating system, web server, database, and programming language.

## 2) Life without Docker

Before Docker, applications were run directly on the host OS, leading to issues with dependency management, environment consistency, and resource conflicts between applications.

## 3) Life with Docker

With Docker, applications are packaged with all their dependencies into containers, ensuring consistent environments across development, testing, and production. This reduces conflicts and simplifies deployment.

## 4) Docker Introduction

Docker is an open-source platform that automates the deployment of applications inside lightweight containers. Containers allow developers to package applications with their dependencies, making them portable and consistent across various environments.

## 5) Virtualization vs Containerization

- **Virtualization**: Involves running multiple OS instances on a single physical server using hypervisors, leading to overhead due to full OS virtualization.
- **Containerization**: Uses containers to run applications in isolated environments on the same OS kernel, offering efficiency and faster performance with minimal overhead.

## 6) Docker Installation in Linux

Installation steps for Docker on a Linux system typically include updating the package repository, installing required packages, adding the Docker repository, and finally installing Docker.

## 7) Docker Architecture

Docker architecture consists of the Docker Engine, which includes the Docker daemon, REST API, and CLI. Containers, images, networks, and volumes are key components managed by Docker.

## 8) Docker Terminology

- **Image**: A lightweight, stand-alone, executable package that includes everything needed to run a piece of software.
- **Container**: A runnable instance of an image.
- **Dockerfile**: A text file containing instructions to build a Docker image.

## 9) Dockerfile & Dockerfile Keywords

A Dockerfile is a script composed of various commands and instructions that define how to build a Docker image. Common keywords include `FROM`, `RUN`, `CMD`, `LABEL`, `EXPOSE`, `ENV`, `ADD`, and `COPY`.

## 10) Writing Dockerfiles

Writing a Dockerfile involves specifying the base image, copying application code, installing dependencies, and defining the entry point for the container.

## 11) Docker Image Commands

Commands such as `docker build`, `docker pull`, and `docker push` are used to create, retrieve, and share Docker images.

## 12) Docker Container Commands

Commands like `docker run`, `docker stop`, `docker rm`, and `docker ps` are used to manage containers.

## 13) Dockerizing Java Spring Boot Application

The process involves creating a Dockerfile that packages a Java Spring Boot application into a Docker image, which can then be run as a container.

## 14) Dockerizing Java Web Application with External Tomcat

This involves deploying a Java web application in a Docker container using an external Tomcat server, typically by copying the WAR file into a Tomcat Docker image.

## 15) Dockerizing Python Flask Application

A Dockerfile is created to package a Python Flask application, including installing the necessary dependencies and setting the Flask application as the container's entry point.

## 16) Docker Network

Docker networking allows containers to communicate with each other and external systems. It includes bridge networks, host networks, and overlay networks for multi-host communication.

## 17) Monolith Vs Microservices

- **Monolith**: A single, unified software application where components are interlinked and interdependent.
- **Microservices**: An architectural style where applications are composed of small, independent services that communicate over a network.

## 18) Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications using a YAML file to configure the application’s services, networks, and volumes.

## 19) Docker Compose File Creation

A Docker Compose file (`docker-compose.yml`) defines the services, networks, and volumes for a multi-container application. Each service specifies the Docker image, ports, volumes, and environment variables.

## 20) Docker Volumes

Docker volumes are used to persist data generated and used by Docker containers. They allow data to be shared between the host and containers or among containers themselves.

## 21) Spring Boot with MySQL DB Dockerization using Docker Compose

A Docker Compose setup that includes a Spring Boot application and a MySQL database, defining each service in the `docker-compose.yml` file and linking them together.

## 22) What is Orchestration?

Orchestration refers to the automated management, coordination, and scaling of containerized applications across a cluster of machines, ensuring high availability and reliability.

## 23) Docker Swarm

Docker Swarm is Docker's native clustering and orchestration tool that manages a cluster of Docker nodes, turning them into a single virtual Docker host.

## 24) Docker Swarm Cluster Setup

Setting up a Docker Swarm cluster involves initializing a Swarm on a manager node, joining worker nodes to the cluster, and deploying services across the cluster.

## 25) Deployed Java Web App as Docker Container using Swarm Cluster

This involves packaging a Java web application into a Docker container and deploying it across a Docker Swarm cluster, providing scalability and high availability.

# <<<--------------------------------Docker Commands Reference--------------------------------->>>>>>>

## Basic Docker Commands

### System Information

- **Show Docker system information**  
  `$ docker info`

### Images

- **List Docker images**  
  `$ docker images`

- **Remove a Docker image**  
  `$ docker rmi <image-name>`

- **Pull a Docker image from a repository**  
  `$ docker pull <image-name>`

### Containers

- **Run a Docker container**  
  `$ docker run <image-name>`

- **Run a container in detached mode with port mapping**  
  `$ docker run -d -p <host-port>:<container-port> <image-name>`

- **Tag an image**  
  `$ docker tag <image-name> <image-tag-name>`

- **Login to Docker**  
  `$ docker login`

- **Push a tagged image to a repository**  
  `$ docker push <image-tag-name>`

### Managing Containers

- **List running containers**  
  `$ docker ps`

- **List all containers (running and stopped)**  
  `$ docker ps -a`

- **Stop a running container**  
  `$ docker stop <container-id>`

- **Remove a container**  
  `$ docker rm <container-id>`

- **Force remove a container**  
  `$ docker rm -f <container-id>`

- **Clean up unused Docker objects**  
  `$ docker system prune -a`

- **View container logs**  
  `$ docker logs <container-id>`

- **Execute a command inside a running container**  
  `$ docker exec -it <container-id> /bin/bash`

## Docker Networks

- **List Docker networks**  
  `$ docker network ls`

- **Create a Docker network**  
  `$ docker network create <network-name>`

- **Remove a Docker network**  
  `$ docker network rm <network-name>`

- **Inspect a Docker network**  
  `$ docker network inspect <network-name>`

## Docker Compose

- **Start Docker Compose services in detached mode**  
  `$ docker-compose up -d`

- **Stop Docker Compose services**  
  `$ docker-compose down`

- **List Docker Compose services**  
  `$ docker-compose ps`

- **List Docker Compose images**  
  `$ docker-compose images`

- **Stop specific Docker Compose services**  
  `$ docker-compose stop`

- **Start specific Docker Compose services**  
  `$ docker-compose start`

## Docker Volumes

- **List Docker volumes**  
  `$ docker volume ls`

- **Create a Docker volume**  
  `$ docker volume create <vol-name>`

- **Inspect a Docker volume**  
  `$ docker volume inspect <vol-name>`

- **Remove a Docker volume**  
  `$ docker volume rm <vol-name>`

- **Clean up unused Docker volumes**  
  `$ docker system prune --volumes`

## Docker Services (Swarm Mode)

- **Create a Docker service**  
  `$ sudo docker service create --name <service-name> -p 8080:8080 <img-name>`

- **Scale a Docker service**  
  `$ sudo docker service scale <service-name>=<replicas>`

- **List Docker services**  
  `$ sudo docker service ls`

- **Remove a Docker service**  
  `$ sudo docker service rm <service-name>`
