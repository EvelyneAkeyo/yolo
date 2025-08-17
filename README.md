# Week 5 Kubernetes Project 🚀

-----

## Overview

This project demonstrates deploying a full-stack application on **Kubernetes**.
The application has three components:

  * **Frontend** → React app served by Nginx
  * **Backend** → Node.js/Express API
  * **Database** → MongoDB (with persistence using StatefulSets + PVC)

All components are containerized with Docker and orchestrated using Kubernetes manifests.

-----

## Tech stack

  * **Kubernetes** (Deployment, Service, StatefulSet, PVC)
  * **Docker** (Containerization)
  * **React** (Frontend UI)
  * **Node.js / Express** (Backend API)
  * **MongoDB** (Database)

-----

## Repository structure

yolo/
│── Manifest/ \# Common Kubernetes manifests
│── week5-k8s-project/ \# Project-specific manifests
│ ├── mongo-deployment.yml
│ ├── backend-deployment.yml
│ ├── frontend-deployment.yml
│── README.md \# Project documentation
│── explanation.md \# Deep dive explanation

```yaml
Copy
Edit
```

-----

## Deployment steps

1.  Clone this repo
    ```bash
    git clone https://github.com/EvelyneAkeyo/yolo.git
    cd yolo
    ```
2.  Apply the Kubernetes manifests
    ```bash
    kubectl apply -f week5-k8s-project/
    ```
3.  Verify deployments
    ```bash
    kubectl get pods
    kubectl get services
    ```
4.  Access the app through the frontend service (NodePort or Ingress, depending on setup).

-----

## Explanation

See `explanation.md` for details about:

  * Why Kubernetes was chosen
  * How services connect frontend → backend → database
  * Persistence strategies for MongoDB
  * Potential improvements

-----

## Learning outcomes

By completing this project, I:

  * Learned to orchestrate multi-tier apps in Kubernetes
  * Understood services, deployments, and persistent storage
  * Practiced writing clear manifests and structuring a project repo
