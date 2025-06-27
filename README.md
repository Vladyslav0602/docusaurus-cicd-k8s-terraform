Docusaurus CI/CD Deployment: Azure Static Web Apps & Kubernetes
This repository demonstrates an automated deployment solution for a Docusaurus documentation site using two distinct CI/CD pipelines in Azure. It showcases expertise in cloud deployment workflows leveraging Docusaurus, Docker, Kubernetes (AKS), and GitHub Actions.


🚀 Getting Started Locally (for Reviewers)
To quickly test and verify the application locally, please ensure you have the following prerequisites installed:



📋 Prerequisites
Git — for cloning this repository.

- Node.js (LTS recommended) and npm — essential for Docusaurus development and build processes.

- Docker Desktop (or Docker Engine) — required for building and running Docker images.

- kubectl — Kubernetes CLI tool to interact with clusters.

- Minikube — for setting up and managing a local Kubernetes cluster to test the Docker + Kubernetes deployment.

- Azure CLI — for authenticating with Azure and managing cloud resources.

1. Clone the Repository
**git clone https://github.com/Vladyslav0602/docusaurus-cicd-k8s-terraform.git**

**cd docusaurus-cicd-k8s-terraform**

(Authentication details including login and token for Karel Fiala will be shared separately via phone.)

2. Install Docusaurus Dependencies and Build Site

**cd my-doc-site**

**npm install**

**npm run build**

**cd ..**

This generates the build/ directory with static files for deployment.

3. Run Docusaurus Locally (Development Server)
For quick verification of the site in development mode:

**cd my-doc-site**

**npm run start**

Open your browser at **http://localhost:3000** to view the site.

☁️ Deployment Options
This project supports two deployment options, each automated through dedicated GitHub Actions workflows.

Deployment Option 1: Azure Static Web App
Deploy the Docusaurus site directly to an Azure Static Web App — a cost-effective, scalable static hosting solution.

Live Application URL:

**https://gray-hill-061f67c10.2.azurestaticapps.net/**

CI/CD Workflow:
The .github/workflows/azure-static-webapp.yml pipeline automates build and deployment on pushes to the main branch.

Deployment Option 2: Kubernetes with Docker (Local Minikube Test)
Containerize and deploy the Docusaurus site inside a Kubernetes cluster. This can be tested locally using Minikube.

Start Minikube Cluster
Ensure Docker is running, then start Minikube with Docker driver:

**minikube start --driver=docker**

Apply Kubernetes Manifests
From the project root:

**kubectl apply -f k8s/deployment.yml**

**kubectl apply -f k8s/service.yml**


Access the Application
Open the service in your default browser:

**minikube service docusaurus-service**

Alternatively, access manually:

**minikube ip**

 Example output: 192.168.49.2

**kubectl get svc docusaurus-service**

 Check the NodePort, e.g. 30432

 Then open:

http://<Minikube_IP>:<NodePort>

 e.g., http://192.168.49.2:30432

🛑 Stop and Delete Minikube Cluster
To stop and delete the Minikube cluster when done testing:

**minikube stop**

**minikube delete**
