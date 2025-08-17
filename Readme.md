🚀 Task 5 – Minikube & Kubernetes Deployment
This repository demonstrates Kubernetes fundamentals using Minikube. The goal of this task is to practice namespace creation, config management, deployments, scaling, and rollouts in a real Kubernetes environment.

📂 Project Structure
task-5-minikube/
├── README.md                # Documentation for this project
└── k8s/                     # Kubernetes manifests
├── namespace.yaml       # Defines a custom namespace
├── configmap.yaml       # Stores application configuration
├── deployment.yaml      # Deploys the app with replicas
└── service.yaml         # Exposes the app as a service
docs/
└── screenshots/             # Output screenshots for verification
├── pods.png
├── services.png
├── scale-3-replicas.png
└── rollout.png

⚙️ Setup & Prerequisites
1. Install Dependencies
Install Docker Desktop (with WSL2 backend enabled).

Install Minikube → Download here.

Install kubectl → Download here.

2. Verify Installations
minikube version
kubectl version --client

▶️ Running the Project
1. Start Minikube
minikube start --driver=docker
kubectl get nodes

Expected: 1 node (minikube) in Ready state.

2. Create Namespace
kubectl apply -f k8s/namespace.yaml
kubectl get namespaces

3. Apply ConfigMap
kubectl apply -f k8s/configmap.yaml
kubectl get configmaps -n <your-namespace>

4. Deploy Application
kubectl apply -f k8s/deployment.yaml
kubectl get pods -n <your-namespace>

5. Expose as Service
kubectl apply -f k8s/service.yaml
kubectl get services -n <your-namespace>

6. Scale the Deployment
kubectl scale deployment my-app --replicas=3 -n <your-namespace>
kubectl get pods -n <your-namespace>

7. Rollout Updates
Update the image in deployment.yaml, then:

kubectl apply -f k8s/deployment.yaml
kubectl rollout status deployment/my-app -n <your-namespace>

📚 Key Learnings
Setting up Minikube with Docker driver.

Organizing Kubernetes manifests (namespace, configmap, deployment, service).

Running deployments, scaling pods, and rolling out updates.

Capturing outputs for documentation.

🤝 Contribution
Fork this repo.

Create a branch (feature/new-change).

Commit your changes.

Open a PR into dev.

📌 Summary
This task provides a hands-on simulation of Kubernetes basics inside Minikube. It mirrors how DevOps engineers deploy, scale, and update applications in real-world clusters.

⚡ This README is now internship-review ready — it’s clean, structured, and professional.
