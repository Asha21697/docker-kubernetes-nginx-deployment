# Docker to Kubernetes Nginx Deployment Pipeline

## Project Overview

This project demonstrates the complete containerization and deployment lifecycle of a web application using Docker and Kubernetes.

A custom Nginx web application was containerized using Docker, published to Docker Hub, and deployed on a Kubernetes multi-node cluster consisting of 1 Master Node and 3 Worker Nodes.

The project covers image creation, container deployment, image registry integration, Kubernetes deployment, service exposure, and application validation.

---

## Project Architecture

```text
Custom HTML Application
          │
          ▼
      Dockerfile
          │
          ▼
    Docker Image
          │
          ▼
   Docker Container
          │
          ▼
     Docker Hub
          │
          ▼
 Kubernetes Deployment
          │
          ▼
 Kubernetes Service
          │
          ▼
     Browser Access
```

---

## Environment

- Operating System: Ubuntu Linux
- Docker Engine
- Docker Hub
- Kubernetes Cluster
- kubeadm
- kubelet
- kubectl
- containerd
- Calico Networking

---

## Project Objectives

- Build a custom Docker image
- Deploy containers using Docker
- Push images to Docker Hub
- Pull images from a remote registry
- Deploy workloads on Kubernetes
- Scale applications using Deployments
- Expose applications using NodePort Services
- Validate end-to-end application accessibility

---

## Docker Implementation

### Verify Docker Installation

```bash
docker --version
```

### Create Dockerfile

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

### Build Docker Image

```bash
docker build -t asha-nginx:v1 .
```

### Verify Images

```bash
docker images
```

### Run Docker Container

```bash
docker run -d --name asha-web -p 8080:80 asha-nginx:v1
```

### Verify Running Container

```bash
docker ps
```

### Validate Application

```text
http://192.168.247.129:8080
```

---

## Docker Hub Integration

### Login to Docker Hub

```bash
docker login
```

### Tag Image

```bash
docker tag asha-nginx:v1 asha21697/asha-nginx:v1
```

### Push Image

```bash
docker push asha21697/asha-nginx:v1
```

### Verify Repository

Image successfully published to Docker Hub and made available for Kubernetes deployments.

---

## Kubernetes Deployment

### Create Deployment

```bash
kubectl create deployment asha-nginx \
--image=asha21697/asha-nginx:v1 \
--replicas=3
```

### Verify Deployment

```bash
kubectl get deployment
```

### Verify Pods

```bash
kubectl get pods -o wide
```

### Expose Application

```bash
kubectl expose deployment asha-nginx \
--type=NodePort \
--port=80
```

### Verify Service

```bash
kubectl get svc
```

---

## Commands Used

```bash
docker --version

docker build -t asha-nginx:v1 .

docker images

docker run -d --name asha-web -p 8080:80 asha-nginx:v1

docker ps

docker login

docker tag asha-nginx:v1 asha21697/asha-nginx:v1

docker push asha21697/asha-nginx:v1

kubectl create deployment asha-nginx \
--image=asha21697/asha-nginx:v1 \
--replicas=3

kubectl get deployment

kubectl get pods -o wide

kubectl expose deployment asha-nginx \
--type=NodePort \
--port=80

kubectl get svc

docker container prune -f

docker image prune -a -f
```

---

## Project Highlights

- Docker Containerization - Containerized a custom Nginx web application using Docker.
- Docker Image Management - Built and managed Docker images using Dockerfile.
- Docker Hub Integration - Published custom images to Docker Hub.
- Container Deployment - Executed and validated containers locally.
- Kubernetes Deployment - Deployed workloads on a Kubernetes multi-node cluster.
- Replica Management - Created Deployments with multiple replicas.
- Service Exposure - Exposed applications using NodePort Services.
- Application Validation - Verified end-to-end browser accessibility.
- Troubleshooting Experience - Resolved Docker authentication and deployment-related issues.
- Resource Optimization - Performed Docker image and container cleanup.
- DevOps Workflow - Demonstrated a complete Docker-to-Kubernetes deployment pipeline.

---

## Skills Demonstrated

- Docker Administration
- Docker Image Management
- Dockerfile Development
- Docker Hub Integration
- Container Lifecycle Management
- Kubernetes Deployments
- Kubernetes Services
- Pod Management
- NodePort Networking
- Linux Administration
- DevOps Fundamentals
- Container Orchestration
- Application Deployment
- Infrastructure Troubleshooting

---

## Screenshots

### Docker Installation Verification

![Docker Version](screenshots/docker-version.png)

### Docker Image Build

![Docker Build](screenshots/docker-build.png)

### Docker Images

![Docker Images](screenshots/docker-images.png)

### Running Docker Container

![Docker Container](screenshots/docker-container.png)

### Docker Hub Push

![Docker Hub Push](screenshots/dockerhub-push.png)

### Kubernetes Deployment

![Deployment](screenshots/kubernetes-deployment.png)

### Running Pods

![Pods](screenshots/kubernetes-pods.png)

### Kubernetes Service

![Service](screenshots/kubernetes-service.png)

### Application Output

![Application](screenshots/nginx-app-working.png)

### Docker Cleanup

![Cleanup](screenshots/docker-cleanup.png)

---

## Troubleshooting Experience

During the implementation of this project, several real-world issues were encountered and resolved:

### Docker Permission Denied Error

- Encountered permission denied while accessing the Docker daemon socket.
- Resolved by executing Docker commands with appropriate privileges.
- Successfully validated Docker installation using the hello-world container.

### Docker Hub Authentication Failure

- Initial Docker login attempts failed due to incorrect credentials.
- Verified Docker Hub account details and retried authentication.
- Successfully established Docker Hub access.

### Docker Image Tagging and Repository Management

- Local Docker images were not accessible to Kubernetes worker nodes.
- Tagged images using Docker Hub repository conventions.
- Published images successfully to a centralized registry.

### Kubernetes Image Pull Validation

- Verified successful image retrieval from Docker Hub.
- Ensured image availability across all worker nodes.
- Confirmed container startup after image download.

### Pod Initialization Monitoring

- Observed pods in ContainerCreating state during deployment.
- Monitored pod lifecycle and image pull progress.
- Verified successful transition to Running state.

### Service Exposure and Accessibility

- Configured Kubernetes NodePort Service.
- Verified service creation and port assignment.
- Successfully accessed the application through the browser.

### Docker Resource Cleanup

- Performed container and image cleanup using Docker prune commands.
- Reclaimed storage space and optimized system resources.
- Verified cleanup using Docker system reports.

### End-to-End Validation

Successfully verified:

- Docker Image Creation
- Docker Container Execution
- Docker Hub Image Publishing
- Kubernetes Deployment Creation
- Pod Scheduling Across Worker Nodes
- NodePort Service Accessibility
- Browser-Based Application Access

## Key Learning Outcomes

- Understanding Docker image creation workflow
- Working with Docker containers and port mapping
- Publishing images to Docker Hub
- Integrating Docker Hub with Kubernetes
- Managing Deployments and ReplicaSets
- Exposing applications using Services
- Understanding container orchestration concepts
- Managing application lifecycle in Kubernetes
- Troubleshooting deployment issues
- Implementing real-world DevOps workflows

---

## Future Enhancements

- Jenkins CI/CD Pipeline
- Helm Package Management
- Prometheus Monitoring
- Grafana Dashboards
- Kubernetes Ingress Controller
- GitHub Actions Automation
- Horizontal Pod Autoscaling
- Kubernetes Persistent Volumes

---

## Author

**ASHA**

Linux | Docker | Kubernetes | DevOps Enthusiast
