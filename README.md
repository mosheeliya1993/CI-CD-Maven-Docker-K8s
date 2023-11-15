# Demo-App-Mosheliya

## Project Overview

This project, `demo-app-mosheliya`, demonstrates a simple web application that returns "Hello World". The application is built using Maven, containerized with Docker, and deployed to a Kubernetes cluster using a Jenkins Declarative Pipeline.

## Prerequisites

- JDK 1.8 or later
- Maven 3.3+
- Docker
- Jenkins with Maven, Docker, and Kubernetes plugins
- Access to a Kubernetes cluster
- A Docker Hub account (or other container registry)

## Repository Structure

- `src/main/java/com/mosheliya/demoapp/`: Application source code.
- `Dockerfile`: Instructions to build the Docker image.
- `Jenkinsfile`: Defines the Jenkins pipeline for CI/CD.
- `k8s-deployment.yml`: Kubernetes deployment and service configuration.
- `pom.xml`: Maven project file with dependencies and build configuration.
- `README.md`: This file, describing the project and setup.

## Building and Running the Application

### Locally

1. To build the project, run:

   ```bash
   mvn clean install
