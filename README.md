# Flappy Bird — Docker & Kubernetes

A browser-based Flappy Bird game containerized with Docker and deployed to a local Kubernetes cluster using Docker Desktop.

## Overview

This project packages a standalone HTML, CSS, and JavaScript game with Nginx, then deploys it to Kubernetes using a Deployment and NodePort Service.

## Technologies

- HTML, CSS, and JavaScript
- Nginx
- Docker
- Kubernetes
- YAML
- Git and GitHub

## Project Structure

```text
flappy-bird-kubernetes/
├── index.html
├── Dockerfile
├── .dockerignore
├── .gitignore
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── screenshots/
└── README.md
```

## Run with Docker

Build the image:

```bash
docker build -t flappy-bird:latest .
```

Run the container:

```bash
docker run -d --name flappy-bird-container -p 8080:80 flappy-bird:latest
```

Open http://localhost:8080 in your browser.

To stop and remove the container:

```bash
docker stop flappy-bird-container
docker rm flappy-bird-container
```

## Deploy with Kubernetes

Apply the Deployment and Service:

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

Check the rollout:

```bash
kubectl rollout status deployment/flappy-bird
kubectl get pods
kubectl get services
```

### Access the application

For local testing, forward the Kubernetes Service to your machine:

```bash
kubectl port-forward service/flappy-bird 8081:80
```

Keep the command running and open http://localhost:8081.

## What I Learned

- Building and running Docker images for a static web application.
- Serving browser-based content with Nginx.
- Defining Kubernetes Deployments and Services using YAML.
- Configuring readiness probes and container resource requests and limits.
- Inspecting Pods, Services, endpoints, and rollout status.
- Troubleshooting local container networking.

## Future Improvements

- Add screenshots and a gameplay preview.
- Improve container image versioning.
- Add automated build and validation checks.
- Explore Kubernetes scaling and rolling updates.