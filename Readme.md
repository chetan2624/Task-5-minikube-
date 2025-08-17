## Task 5 - Minikube & Kubernetes Deployment

This repository serves as a hands-on project to demonstrate the fundamentals of **Kubernetes** using **Minikube**. The project focuses on practical skills essential for a DevOps role, including namespace creation, config management, deployments, scaling, and rolling out updates.

-----

## 📂 Project Structure

```
task-5-minikube/
├── README.md                 # Project documentation
└── k8s/                      # Kubernetes manifest files
    ├── namespace.yaml        # Defines a custom namespace
    ├── configmap.yaml        # Stores application configuration
    ├── deployment.yaml       # Deploys the application with specified replicas
    └── service.yaml          # Exposes the application as a service
└── docs/                     # Documentation and output screenshots
    └── screenshots/          # Verification screenshots
        ├── pods.png
        ├── services.png
        ├── scale-3-replicas.png
        └── rollout.png
```

-----

## ⚙️ Setup & Prerequisites

Before you begin, ensure you have the following tools installed:

1.  **Docker Desktop** (with WSL2 backend enabled for Windows)
2.  **Minikube** - A tool that runs a single-node Kubernetes cluster locally.
3.  **kubectl** - The command-line tool for interacting with Kubernetes clusters.

You can verify your installations by running the following commands:

```powershell
minikube version
kubectl version --client
```

-----

## ▶️ Running the Project

Follow these steps to deploy and manage the application in your Minikube environment.

### 1\. Start Minikube

Start your local Kubernetes cluster using the Docker driver. This will create a single-node cluster named `minikube`.

```bash
minikube start --driver=docker
kubectl get nodes
```

Expected output: A single node named `minikube` in a **Ready** state.

### 2\. Create Namespace

Apply the `namespace.yaml` manifest to create a dedicated namespace for this project, which helps in resource isolation.

```bash
kubectl apply -f k8s/namespace.yaml
kubectl get namespaces
```

### 3\. Apply ConfigMap

Apply the `configmap.yaml` manifest to create a ConfigMap. This stores non-confidential configuration data for your application.

```bash
kubectl apply -f k8s/configmap.yaml
kubectl get configmaps -n demo
```

Remember to replace `demo` with the name of the namespace you created.

### 4\. Deploy Application

Apply the `deployment.yaml` manifest. This will deploy the application and create the specified number of pods.

```bash
kubectl apply -f k8s/deployment.yaml
kubectl get pods -n <your-namespace>
```

  * 📸 See `docs/screenshots/pods.png` for a visual example.

### 5\. Expose as Service

Apply the `service.yaml` manifest to create a Service. This exposes the application to the network and enables load balancing across your pods.

```bash
kubectl apply -f k8s/service.yaml
kubectl get services -n <your-namespace>
```

  * 📸 See `docs/screenshots/services.png` for a visual example.

### 6\. Scale the Deployment

Scale the number of application replicas to 3 using the `kubectl scale` command.

```bash
kubectl scale deployment my-app --replicas=3 -n <your-namespace>
kubectl get pods -n <your-namespace>
```

  * 📸 See `docs/screenshots/scale-3-replicas.png` for a visual example.

### 7\. Rollout Updates

To perform a rolling update, first, modify the image tag in `k8s/deployment.yaml`. After saving the changes, apply the updated manifest. Kubernetes will then intelligently replace the old pods with new ones without downtime.

```bash
kubectl apply -f k8s/deployment.yaml
kubectl rollout status deployment/my-app -n <your-namespace>
```

  * 📸 See `docs/screenshots/rollout.png` for a visual example.

-----

## ✅ Key Learnings

This project provides practical experience with several key Kubernetes concepts:

  * Setting up a local development environment with **Minikube** and **Docker**.
  * Structuring and applying **Kubernetes manifests** for different resource types (`Namespace`, `ConfigMap`, `Deployment`, `Service`).
  * Executing common Kubernetes operations like **deploying**, **scaling**, and performing **rollouts**.
  * Documenting and capturing project outputs for verification and reference.

-----

## 🤝 Contribution

Contributions are welcome\! Please follow these steps:

1.  Fork the repository.
2.  Create a new branch (`git checkout -b feature/your-feature-name`).
3.  Commit your changes (`git commit -m 'feat: Add your feature'`).
4.  Push to the branch (`git push origin feature/your-feature-name`).
5.  Open a **Pull Request** to the `dev` branch.

-----

## 📌 Summary

This repository is an excellent starting point for anyone looking to understand the fundamentals of application deployment and management in a Kubernetes environment. By completing this task, you'll gain hands-on experience that mirrors real-world DevOps practices.
