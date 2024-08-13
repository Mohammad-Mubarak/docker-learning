# docker-learning

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

````bash
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
````





# Docker Commands

## Basic Docker Information

- **See Docker information:**

  ```bash
  docker info


- **List Docker images:**

   ```bash
  docker images


- **Pull the hello-world Docker image:**

   ```bash
  docker pull hello-world

- **Run the hello-world Docker image:**

   ```bash
  docker run hello-world

- **Display running Docker containers:**

   ```bash
  docker ps

- **Display running and stopped containers:**

   ```bash
  docker ps -a

- **Inspect a Docker image:**

   ```bash
  docker inspect <image-id>

- **Remove a Docker image:**

   ```bash
  docker rmi <image-name / image-id>

- **Forcefully remove a Docker image:**

   ```bash
  docker rmi -f <image-name / image-id>

- **Stop a running container:**

   ```bash
  docker stop <container-id>

- **Remove a Docker container:**

   ```bash
  docker rm <container-id>

- **Remove all stopped containers, unused images, and unused networks:**

   ```bash
  docker system prune -a
````
