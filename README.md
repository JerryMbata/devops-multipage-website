# DevOps Portal - Kubernetes Ingress Project

## Project Overview

This project demonstrates how to deploy a multi-page web application using:

- Docker
- Nginx Web Server
- Kubernetes
- Kubernetes Services
- Nginx Ingress Controller
- Jenkins CI/CD Pipeline
- GitHub

The application contains multiple pages that communicate through Kubernetes Ingress routing.

---

# Architecture

            User Browser
                 |
                 |
         Nginx Ingress Controllers
                 |
    --------------------------------
    |              |              |
    |              |              |


---

# Application Pages

The project contains:

## Home Page

Route:


Description:

Main landing page with links to other pages.

---

## About Page

Route:


Description:

Contains company information.

---

## Services Page

Route:


Description:

Displays available DevOps services.

---

## Contact Page

Route:


Description:

Contains contact information.

---

# Technology Stack

| Technology | Purpose |
|------------|---------|
| HTML | Website pages |
| Nginx | Web server |
| Docker | Containerization |
| Kubernetes | Container orchestration |
| Ingress Controller | Traffic routing |
| Jenkins | CI/CD automation |
| GitHub | Source code management |
| Docker Hub | Image repository |


---

# Project Structure

[200~devops-portal/

├── home/
│ ├── index.html
│ └── Dockerfile
│
├── about/
│ ├── index.html
│ └── Dockerfile
│
├── services/
│ ├── index.html
│ └── Dockerfile
│
├── contact/
│ ├── index.html
│ └── Dockerfile
│
├── kubernetes/
│ ├── home.yaml
│ ├── about.yaml
│ ├── services.yaml
│ ├── contact.yaml
│ └── ingress.yaml
│
└── Jenkinsfile


---

# Docker Build

Build Docker images:

```bash
docker build -t jerrymbata1/home-page:v1 ./home

docker build -t jerrymbata1/about-page:v1 ./about

docker build -t jerrymbata1/services-page:v1 ./services

docker build -t jerrymbata1/contact-page:v1 ./contact

docker login

docker push jerrymbata1/home-page:v1

docker push jerrymbata1/about-page:v1

docker push jerrymbata1/services-page:v1

docker push jerrymbata1/contact-page:v1

---

# Apply Kubernetes manifests:

kubectl apply -f kubernetes/

-------------

# Ingress Routing

/
        ---> home-service

/about
        ---> about-service

/services
        ---> services-service

/contact
        ---> contact-service


# Jenkins CI/CD Pipeline

The Jenkins pipeline automates:

1. Pulling source code from GitHub
2. Building Docker images
3. Pushing images to Docker Hub
4. Deploying application to Kubernetes

GitHub
   |
   |
 Jenkins
   |
   |
 Docker Build
   |
   |
 Docker Hub
   |
   |
 Kubernetes Deployment

------------------

# Skills Demonstrated

This project demonstrates:

✅ Containerization with Docker
✅ Kubernetes Deployments
✅ Kubernetes Services
✅ Ingress Routing
✅ CI/CD Automation
✅ Git Workflow
✅ Infrastructure Deployment
✅ Cloud Native Application Deployment 

---------------------

# Author

Jerry Mbata

DevOps Engineer | Cloud | Kubernetes | CI/CD
