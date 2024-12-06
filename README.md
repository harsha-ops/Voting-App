# Voting App Microservices

This is a simple microservice-based application for voting, built using Docker and deployed to a Kubernetes cluster (Minikube) using Jenkins CI/CD pipelines. The application consists of three microservices: **Vote**, **Worker**, and **Result**.

## Getting Started

Follow the steps below to get started with building, deploying, and running the Voting App.

### 1. Write Dockerfiles for Each Microservice

To containerize each of the microservices (Vote, Worker, and Result), you will need to create a Dockerfile for each service. Below are the key services:

- **Vote Microservice**: Written in Python language, Handles receiving votes from users and adding them to a queue.
- **Worker Microservice**: Written in .Net, Processes the votes from the queue and updates the database.
- **Result Microservice**: Written in JavaScript, Displays the voting results.

Each microservice will have its own Dockerfile that defines the environment, dependencies, and how to run the service.

### 2. Write Jenkins Pipelines for Each Microservice

For each microservice, write a **Jenkinsfile** that defines the stages required for building, pushing, and deploying the Docker images.

The pipeline will consist of the following stages:

- **Checkout the source code**: Pull the latest source code from GitHub.
- **Build the Docker images**: Use the `Dockerfile` to build the Docker image for the respective microservice.
- **Push the Docker images to Docker Hub**: Push the built Docker image to Docker Hub registry.
- **Deploy the Docker image to Kubernetes (Minikube)**: Deploy the Docker image from Docker Hub to a running Minikube Kubernetes cluster.

### 3. Create Jenkins Jobs for Each Microservice
Once you have the Jenkinsfile ready for each microservice, create a separate Jenkins job for each microservice in the Jenkins dashboard:

Create a new Pipeline job for each microservice.
In the job configuration, link the job to the GitHub repository containing the source code.
Set up the pipeline to point to the corresponding Jenkinsfile in the repository.
Configure any necessary Jenkins credentials (e.g., for Docker Hub login).
Trigger the pipeline to build, push, and deploy the Docker images.

### 4. Set Up Kubernetes (Minikube) Cluster
Ensure that you have a running Minikube Kubernetes cluster.

### 5. Deploy Microservices to Kubernetes
After pushing the Docker images to Docker Hub, deploy each microservice to your Minikube Kubernetes cluster by applying the corresponding Kubernetes deployment and service YAML files.


## Architecture

![Architecture diagram](architecture.excalidraw.png)

* A front-end web app in [Python](/vote) which lets you vote between two options
* A [Redis](https://hub.docker.com/_/redis/) which collects new votes
* A [.NET](/worker/) worker which consumes votes and stores them in…
* A [Postgres](https://hub.docker.com/_/postgres/) database backed by a Docker volume
* A [Node.js](/result) web app which shows the results of the voting in real time

### Key Notes:
- Make sure your **Jenkins** server has the necessary plugins installed (e.g., Docker, Kubernetes, GitHub integration).
- Configure **Docker Hub credentials** and **Kubernetes credentials** in Jenkins for smooth integration.



