# 🚀 Enterprise-Grade Kubernetes DevSecOps & Observability Platform

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)


📖 Overview
This repository provides a comprehensive Infrastructure as Code (IaC) and DevSecOps framework for deploying a highly available microservices application (Super Mario demo) on a Kubernetes cluster.

Moving beyond basic deployment, this architecture is engineered to production-grade standards. It prioritizes a Zero-Trust Security model, enforces shift-left vulnerability scanning, and integrates a full-stack telemetry and observability suite to monitor cluster health in real time.

🏗️ Core Architecture & Features
This platform is engineered around four core DevOps pillars:

Container Orchestration: Deployed on Kubernetes leveraging Deployments, NodePort/ClusterIP Services, and Persistent Volume Claims (PVC) to ensure state management, high availability, and fault tolerance.

Continuous Integration & Delivery (CI/CD): Fully automated Git-driven workflows utilizing GitHub Actions for immutable image building, secure authentication, and artifact pushing to Docker Hub.

DevSecOps & Zero-Trust: * Static Application Security Testing (SAST): Trivy vulnerability scanning integrated directly into the pipeline to block critical CVEs from reaching production.

Network Segmentation: Custom Kubernetes Network Policies to ensure strict pod-to-pod traffic isolation.

Access Control: Implementation of Role-Based Access Control (RBAC) adhering to the principle of least privilege.

Observability & Telemetry: Advanced monitoring stack provisioned via Helm Charts, utilizing Prometheus for metrics aggregation and Grafana for real-time visualization of cluster resources.

🛠️ Technology Stack
Infrastructure & Orchestration: Kubernetes (K3d), Kubectl

Containerization: Docker, Docker Hub

Automation & CI/CD: GitHub Actions

Security & Compliance: Aqua Security Trivy, Kubernetes RBAC, Network Policies

Observability Stack: Prometheus, Grafana, Helm

⚙️ CI/CD Pipeline Workflow
The automated deployment pipeline is triggered on every push to the main branch, enforcing strict quality and security gates:

Checkout & Setup: Initializes the environment and pulls the latest source code.

Secure Authentication: Executes Docker Login utilizing encrypted GitHub Secrets to prevent credential leakage.

Build & Containerize: Compiles an optimized Docker image and prepares it for distribution.

Security Gate (Trivy): Intercepts the image to scan for vulnerabilities. The pipeline is configured to automatically fail if "Critical" or "High" risk CVEs are detected, safeguarding the production environment.

Artifact Push: Upon passing the security gate, the verified image is pushed to the container registry.

📈 Observability & Dashboards
The integrated Grafana dashboards provide continuous insights into the cluster's operational state:

Real-time CPU and Memory consumption per Pod.

Cluster-wide Node health, capacity, and utilization status.

Network throughput and request metrics for the active deployment.

🔧 Installation & Deployment

Prerequisites
Ensure your local environment has the following installed:

Docker

K3d & kubectl

Helm (Optional, for managing the observability stack)

Quick Start Guide

1. Clone the repository:

Bash
git clone https://github.com/marioscloud/k8s-devsecops-observability.git
cd k8s-devsecops-observability

2. Provision the Kubernetes Cluster:

Bash
k3d cluster create mario-cluster -p "8080:80@loadbalancer"

3. Apply Infrastructure Manifests:
Deploy the application, network policies, and persistent storage:

Bash
kubectl apply -f .

4. Verify Deployment:

Bash
kubectl get pods,svc,networkpolicy -A
Author: [Mario Araos]
Cloud & DevOps Engineer | CKA | LFCS | Passionate about resilient infrastructure, DevSecOps, and automation.
