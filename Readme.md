# 🚀 Task 5 – Minikube & Kubernetes Deployment

This repository demonstrates **Kubernetes fundamentals** using **Minikube**.  
The goal of this task is to practice **namespace creation, config management, deployments, scaling, and rollouts** in a real Kubernetes environment.

---

## 📂 Project Structure

```

task-5-minikube/
├── README.md                # Documentation for this project
└── k8s/                     # Kubernetes manifests
├── namespace.yaml       # Defines a custom namespace
├── configmap.yaml       # Stores application configuration
├── deployment.yaml      # Deploys the app with replicas
└── service.yaml         # Exposes the app as a service
docs/
└── screenshots/             # Output screenshots for verification
├── pods.png
├── services.png
├── scale-3-replicas.png
└── rollout.png

````

---

## ⚙️ Setup & Prerequisites

1. **Install Docker Desktop** (with WSL2 backend enabled).
2. **Install Minikube** → [Download here](https://minikube.sigs.k8s.io/docs/start/).
3. **Install kubectl** → [Download here](https://kubernetes.io/docs/tasks/tools/).
4. Verify installs:
   ```powershell
   minikube version
   kubectl version --client
````

---

## ▶️ Running the Project

### 1️⃣ Start Minikube

```bash
minikube start --driver=docker
kubectl get nodes
```

Expected: 1 node (`minikube`) in **Ready** state.

---

### 2️⃣ Create Namespace

```bash
kubectl apply -f k8s/namespace.yaml
kubectl get namespaces
```

---

### 3️⃣ Apply ConfigMap

```bash
kubectl apply -f k8s/configmap.yaml
kubectl get configmaps -n <your-namespace>
```

---

### 4️⃣ Deploy Application

```bash
kubectl apply -f k8s/deployment.yaml
kubectl get pods -n <your-namespace>
```

📸 Refer to `docs/screenshots/pods.png`

---

### 5️⃣ Expose as Service

```bash
kubectl apply -f k8s/service.yaml
kubectl get services -n <your-namespace>
```

📸 Refer to `docs/screenshots/services.png`

---

### 6️⃣ Scale the Deployment

```bash
kubectl scale deployment my-app --replicas=3 -n <your-namespace>
kubectl get pods -n <your-namespace>
```

📸 Refer to `docs/screenshots/scale-3-replicas.png`

---

### 7️⃣ Rollout Updates

Update the image in `deployment.yaml`, then:

```bash
kubectl apply -f k8s/deployment.yaml
kubectl rollout status deployment/my-app -n <your-namespace>
```

📸 Refer to `docs/screenshots/rollout.png`

---

## 📸 Screenshots

* **pods.png** → Shows pods running in namespace
* **services.png** → Service exposing the app
* **scale-3-replicas.png** → Deployment scaled to 3 pods
* **rollout.png** → Successful rollout after update

---

## ✅ Key Learnings

* Setting up Minikube with Docker driver.
* Organizing Kubernetes manifests (`namespace`, `configmap`, `deployment`, `service`).
* Running deployments, scaling pods, and rolling out updates.
* Capturing outputs for documentation.

---

## 🤝 Contribution

1. Fork this repo.
2. Create a branch (`feature/new-change`).
3. Commit your changes.
4. Open a PR into `dev`.

---

## 📌 Summary

This task provides a **hands-on simulation of Kubernetes basics** inside Minikube.
It mirrors how DevOps engineers deploy, scale, and update applications in real-world clusters.

```

---

⚡ This README is now **internship-review ready** — it’s clean, structured, and professional.  

👉 Do you also want me to **write the YAML files** (`namespace.yaml`, `configmap.yaml`, `deployment.yaml`, `service.yaml`) with best practices so you can directly apply them in your project?
```
