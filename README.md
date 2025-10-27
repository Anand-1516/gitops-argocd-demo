# Implemented GitOps Pipeline using ArgoCD and Kubernetes

## 🚀 Overview
This project demonstrates a **GitOps workflow** that automates Kubernetes deployments using **ArgoCD**, **Docker**, and **GitHub**.  
Every Git commit automatically syncs to the Kubernetes cluster through ArgoCD, ensuring **continuous delivery** and **configuration consistency**.

---

## 📁 Project Structure
gitops-argocd-demo/
├── app/
│ ├── Dockerfile
│ ├── package.json
│ └── server.js
│
├── k8s/
│ ├── base/
│ │ ├── deployment.yaml
│ │ ├── service.yaml
│ │ └── kustomization.yaml
│ │
│ └── overlays/
│ └── prod/
│ ├── kustomization.yaml
│ └── image-update-patch.yaml
│
└── argocd/
└── application.yaml

yaml
Copy code

---

## 🧰 Tools & Technologies
- **Kubernetes (Minikube)**
- **ArgoCD**
- **Docker & DockerHub**
- **Git & GitHub**
- **Node.js (Sample Application)**
- **Kustomize**

---

## ⚙️ Setup Steps

### 1. Start Minikube
```bash
minikube start

2. Install ArgoCD
bash
Copy code
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

3. Build and Push Docker Image
bash
Copy code
cd app
docker build -t anand1516/gitops-demo:0.1.0 .
docker push anand1516/gitops-demo:0.1.0

4. Deploy Application via ArgoCD
bash
Copy code
kubectl apply -f argocd/application.yaml

5. Access the Application
bash
Copy code
minikube service gitops-demo --url
🔄 Update Workflow
Update image tag in k8s/overlays/prod/image-update-patch.yaml

Commit and push to GitHub:

bash
Copy code
git add .
git commit -m "bump image to 0.2.0"
git push
ArgoCD auto-syncs and redeploys the new version.

🖼️ Deliverables
✅ GitHub repository with manifests and app code

✅ ArgoCD screenshots showing sync and health

✅ Output screenshots before & after image update

🧠 Key Learning
Git as the single source of truth for deployment

ArgoCD ensures automated sync and rollback

Declarative, auditable, and consistent infrastructure

💼 Resume Line
Implemented GitOps pipeline using ArgoCD and Kubernetes to automate application deployment from Git commits with real-time sync and rollback capabilities.