1. Introduction

This project demonstrates how to deploy a **full-stack application** on a Kubernetes cluster. The app consists of:

* **Frontend (React + Nginx)**
* **Backend (Node.js/Express API)**
* **Database (MongoDB)**

The goal was to practice container orchestration, scaling, and service discovery in Kubernetes.

---

## 2. Architecture



This section would typically include a diagram illustrating how the frontend, backend, and database interact within the Kubernetes environment, showing the flow of data and communication paths.

---

## 3. Kubernetes resources used

1.  Deployment

    Used for the frontend and backend

    Ensures the application runs with the desired number of replicas

2.  StatefulSet

    Used for MongoDB

    Provides stable network identity and persistent storage

3.  PersistentVolumeClaim (PVC)

    Ensures MongoDB data is stored even if pods restart

4.  Service

    **ClusterIP** for internal communication (backend ↔ database)

    **NodePort** or **LoadBalancer** for external access to the frontend

---

## 4. How the application works

The **frontend** (React) communicates with the **backend API** (Node.js)

The **backend** fetches and stores data in **MongoDB**

Kubernetes manages pod creation, scaling, and communication between these components

---

## 5. Challenges Faced

Writing YAML files correctly (indentation is critical)

Understanding the difference between **Deployment** and **StatefulSet**

Making services communicate across pods

---

## 6. Key learnings

How to structure Kubernetes manifests

Difference between stateless and stateful workloads

The importance of persistence in databases

How services expose applications inside/outside the cluster

---

## 7. Project overview

This project was a good introduction to **real-world Kubernetes deployments**

It showed how microservices can be deployed, scaled, and managed efficiently using Kubernetes
