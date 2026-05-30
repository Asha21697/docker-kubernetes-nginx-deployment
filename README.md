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

- Containerized a custom Nginx web application using Docker
- Built Docker images using Dockerfile
- Managed Docker containers and networking
- Published images to Docker Hub
- Integrated Docker Hub with Kubernetes
- Deployed applications on a Kubernetes cluster
- Created Kubernetes Deployments with multiple replicas
- Exposed applications using NodePort Services
- Verified workload scheduling across worker nodes
- Validated end-to-end application accessibility
- Performed Docker image and container cleanup
- Demonstrated practical DevOps deployment workflow

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
