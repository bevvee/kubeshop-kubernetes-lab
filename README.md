# KubeShop – Kubernetes Deployment Lab

<div align="center">

**A hands-on Kubernetes project focused on containerization, orchestration, deployment, and DevOps practices.**

<br/>

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![Minikube](https://img.shields.io/badge/Minikube-2F80ED?logo=kubernetes&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?logo=linux&logoColor=black)

</div>

---

## About the Project

**KubeShop** is a practical project designed to explore Kubernetes and DevOps concepts by deploying a containerized e-commerce application.

The main objective is to understand how applications are packaged, deployed, exposed, scaled, and managed inside a Kubernetes cluster.

The project starts with a frontend application and progressively introduces backend services, database management, networking, persistent storage, Helm, and CI/CD automation.

This repository also serves as a practical learning journey, documenting each implementation step and the Kubernetes concepts behind it.

## Project Objectives

- Understand Kubernetes architecture and core components.
- Containerize applications using Docker.
- Create and manage a local Kubernetes cluster with Minikube.
- Deploy applications using Kubernetes manifests.
- Configure Deployments, Pods, and Services.
- Manage application configuration and sensitive information.
- Implement persistent storage for database workloads.
- Expose applications using Kubernetes Ingress.
- Package applications using Helm.
- Explore CI/CD automation with GitHub Actions.

## Technologies & Tools

| Technology     | Purpose                           |
| -------------- | --------------------------------- |
| Kubernetes     | Container orchestration           |
| Minikube       | Local Kubernetes cluster          |
| Docker         | Application containerization      |
| kubectl        | Kubernetes cluster management     |
| Nginx          | Frontend web server               |
| YAML           | Kubernetes configuration          |
| Helm           | Kubernetes package management     |
| Git & GitHub   | Version control and collaboration |
| GitHub Actions | CI/CD automation (planned)        |

## Project Architecture

The project is being developed progressively.

### Current architecture

The first implementation deploys a frontend application inside a local Kubernetes cluster.

```text
                 KubeShop
                     |
              Kubernetes Cluster
                     |
              +--------------+
              |   Node       |
              |  (Minikube)  |
              +--------------+
                     |
              Frontend Service
                 (NodePort)
                     |
             +-------+-------+
             |               |
         Frontend Pod    Frontend Pod
          (Nginx)         (Nginx)
```

The frontend Deployment runs two replicas to demonstrate Kubernetes workload management.

### Planned architecture

The next stages will introduce backend services, PostgreSQL, persistent storage, and external HTTP routing.

## Repository Structure

```text
kubeshop-kubernetes-lab/
│
├── frontend/
│   ├── Dockerfile
│   └── index.html
│
├── backend/
│
├── kubernetes/
│   ├── namespace.yaml
│   ├── frontend-deployment.yaml
│   ├── frontend-service.yaml
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── postgres-statefulset.yaml
│   ├── postgres-service.yaml
│   ├── postgres-pvc.yaml
│   ├── configmap.yaml
│   ├── secret.yaml
│   └── ingress.yaml
│
├── helm/
│
├── .github/
│   └── workflows/
│
└── README.md
```

## Getting Started

### Prerequisites

Make sure you have installed:

- Docker
- Minikube
- kubectl
- Git

A Linux environment or WSL2 with Docker Desktop is recommended for this setup.

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/kubeshop-kubernetes-lab.git

cd kubeshop-kubernetes-lab
```

### 2. Start the Kubernetes cluster

```bash
minikube start --driver=docker
```

Verify the cluster:

```bash
kubectl get nodes
```

### 3. Create the namespace

```bash
kubectl apply -f kubernetes/namespace.yaml
```

### 4. Build the frontend Docker image

```bash
docker build -t kubeshop-frontend:v1 ./frontend
```

Load the image into Minikube:

```bash
minikube image load kubeshop-frontend:v1
```

### 5. Deploy the frontend

```bash
kubectl apply -f kubernetes/frontend-deployment.yaml

kubectl apply -f kubernetes/frontend-service.yaml
```

### 6. Verify the deployment

```bash
kubectl get pods -n kubeshop

kubectl get deployments -n kubeshop

kubectl get services -n kubeshop
```

### 7. Access the application

Forward the frontend Service to your local machine:

```bash
kubectl port-forward -n kubeshop svc/frontend-service 8080:80
```

Open your browser:

```text
http://localhost:8080
```

## Current Progress

This project is actively under development.

- [x] Create the project structure.
- [x] Set up a local Kubernetes cluster using Minikube.
- [x] Create a Dockerfile for the frontend.
- [x] Build and load the frontend Docker image into Minikube.
- [x] Create a Kubernetes Namespace.
- [x] Deploy the frontend using a Deployment.
- [x] Configure two frontend replicas.
- [x] Expose the frontend using a Kubernetes Service.
- [x] Access the application using port-forwarding.
- [ ] Deploy the backend application.
- [ ] Deploy PostgreSQL using StatefulSet.
- [ ] Configure persistent storage using PVC.
- [ ] Manage configuration using ConfigMaps and Secrets.
- [ ] Configure Ingress for HTTP routing.
- [ ] Create Helm charts.
- [ ] Implement CI/CD with GitHub Actions.
- [ ] Complete documentation and deployment testing.

## What I Am Learning

Through this project, I am exploring:

- Kubernetes Cluster, Nodes, Pods, and Containers.
- Control Plane and Worker Node architecture.
- Deployments, ReplicaSets, and Services.
- Kubernetes networking and service discovery.
- ConfigMaps, Secrets, and persistent volumes.
- Ingress controllers and HTTP routing.
- Helm charts and application packaging.
- CI/CD concepts and deployment automation.

## Future Improvements

The project will continue to evolve with:

1. Complete frontend and backend integration.
2. Database deployment and persistent data management.
3. Ingress configuration and application routing.
4. Helm-based application deployment.
5. Automated build and deployment pipelines.
6. Monitoring and logging integration.

## Author

**Mohammed Amine EL AAZZOUZI**

- GitHub: [@bevvee](https://github.com/bevvee)
- LinkedIn: [Mohammed Amine EL AAZZOUZI](https://www.linkedin.com/in/medelaazzouzi/)

---

\<p align="center">
&#x20; \<strong>Learning by building, one deployment at a time.\</strong>
\</p>
