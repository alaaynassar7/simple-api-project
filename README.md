# 🚀 Simple API Project – OpenShift Multi-Deployment Strategies

A hands-on DevOps project demonstrating how to deploy the **same simple API** using **multiple OpenShift deployment strategies** across **three different technologies**.

This project focuses on **platform usage, deployment patterns, and container workflows** rather than application complexity.

---

## 🧭 Project Overview

The objective of this project is to explore and apply different **OpenShift deployment mechanisms** by deploying a minimal API implemented in:

- 🐍 **Python (Flask)**
- 🟢 **Node.js (Express)**
- 🐘 **PHP (Apache)**

Each application exposes the same endpoints and is deployed using **multiple OpenShift approaches** to highlight differences and use cases.

OpenShift was used to **build, deploy, and validate** the workloads, while this GitHub repository contains the **source code and manifests representing those deployments**.

---

## 🔌 API Endpoints

Each application exposes the following endpoints:

| Endpoint | Description |
|--------|------------|
| `/health` | Health check endpoint |
| `/message` | Returns a static message |
| `/date` | Returns current date and time |

Example response:

<img width="1920" height="1025" alt="image" src="https://github.com/user-attachments/assets/be673493-013b-4b73-bb0b-5c032ddec393" />

---
<img width="1920" height="1028" alt="image" src="https://github.com/user-attachments/assets/5f77657e-91e2-4cd8-a213-97935ae8c704" />

---

<img width="1920" height="1033" alt="image" src="https://github.com/user-attachments/assets/a8fd0d3d-0733-475c-a246-124b0c7a3719" />

---

## 🏗️ Architecture Overview

- ☸️ **OpenShift Sandbox** – Application platform
- 📦 **Containers** – Application runtime
- 🔁 **ImageStreams** – Image lifecycle management
- 📄 **YAML Manifests** – Raw Kubernetes/OpenShift deployments
- 📦 **OpenShift Templates** – Reusable deployment templates
- 🐳 **Dockerfile** – Manual image build workflow
- 🗄️ **RedHat Quay** – External container registry
- 🧠 **GitHub** – Source code & manifest repository

---

## 🔐 Security & Runtime Notes

- Applications run as **non-root users**
- Root user is **not responsible for running the containers**
- Security Context Constraints (SCC) are enforced by OpenShift
- Platform-managed networking and routing is used

---

## 🚀 Deployment Strategies Implemented

The same API was deployed using **four different OpenShift strategies**:

### 1️⃣ Source-to-Image (S2I)
- OpenShift builds the image directly from source code
- Deployed using `oc new-app`

### 2️⃣ Deployment Using YAML
- Manual Kubernetes/OpenShift manifests
- Includes:
  - Deployment
  - Service
  - Route
- Liveness & readiness probes configured

### 3️⃣ OpenShift Templates
- Reusable templates bundling multiple resources
- Simplifies repeated deployments

### 4️⃣ ImageStream + oc new-app
- Images managed via OpenShift ImageStreams
- Deployments created from ImageStreams using `oc new-app`

---

## 🐳 Docker & RedHat Quay Integration

- A **Dockerfile** was written manually
- OpenShift Docker strategy build was used
- Images were built by OpenShift
- Images were **pushed to RedHat Quay**
- Authentication handled using a **Quay Robot Account**

This demonstrates:
- OpenShift-managed builds
- Manual Dockerfile workflows
- External registry integration

---
## 🔗 Live OpenShift Routes

The following URLs were exposed using OpenShift Routes to validate the deployments:

### 🐍 Flask (Python)
- Health:  
  http://flask-api-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/health
- Message:  
  http://flask-api-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/message
- Date:  
  http://flask-api-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/date

---

### 🟢 Node.js
- Health:  
  http://node-api-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/health
- Message:  
  http://node-api-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/message
- Date:  
  http://node-api-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/date

---

### 🐘 PHP
- Health:  
  http://php-api-yaml-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/health.php
- Message:  
  http://php-api-yaml-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/message.php
- Date:  
  http://php-api-yaml-alaaynassar-dev.apps.rm3.7wse.p1.openshiftapps.com/date.php

---
## 📂 Project Structure

```text
simple-api-project/
├── flask/
│   ├── s2i/
│   │   ├── app.py
│   │   ├── requirements.txt
│   │   └── Dockerfile
│   │
│   ├── yaml/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── route.yaml
│   │
│   ├── templates/
│   │   └── flask-template.yaml
│   │
│   └── imagestream/
│
├── nodejs/
│   ├── s2i/
│   │   ├── app.js
│   │   └── package.json
│   │
│   ├── yaml/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── route.yaml
│   │
│   ├── templates/
│   │   └── node-template.yaml
│   │
│   └── imagestream/
│
├── php/
│   ├── s2i/
│   │   ├── index.php
│   │   ├── health.php
│   │   ├── message.php
│   │   └── date.php
│   │
│   ├── yaml/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   └── route.yaml
│   │
│   ├── templates/
│   │   └── php-template.yaml
│   │
│   └── imagestream/
│
└── README.md

