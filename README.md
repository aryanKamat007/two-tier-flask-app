## _Two-tier-flask-app_

This is a simple two-tier application built with **Flask** (Python) and **MySQL**. It is containerized using Docker, deployed on **Amazon EKS (Elastic Kubernetes Service)** using Kubernetes manifests and Helm charts.

## _🧰 Tech Stack_

- 🐍 Python (Flask)
- 🐬 MySQL
- 🐳 Docker
- ☸️ Kubernetes (AWS EKS)
- 🧙 Helm

## _Run locally using Docker_

### 1. Clone the repo
```bash
git clone https://github.com/aryanKamat007/two-tier-flask-app.git
```

### 2. Create the messages table in your MySQL database:
```bash
CREATE TABLE messages (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message TEXT
);
```

### 3. Start the containers using Docker Compose
```bash
docker-compose up --build
```

### 4. Access the app
 - Open your browser and go to: http://localhost:5000


## _☸️ Run on Kubernetes using Helm (EKS or any K8s Cluster)_

📦 Pre-requisites:
 - Kubernetes cluster (EKS, Kubeadm, kind, etc.)
 - kubectl configured
 - helm installed
 - Docker image pushed to Docker Hub or other registry

### 1. Clone the repo
```bash
git clone https://github.com/aryanKamat007/two-tier-flask-app.git
```

### 2. Update the image in helm-charts/two-tier-app/values.yaml:
```bash
flaskapp:
  image:
    repository: your-dockerhub-username/todo-app
    tag: latest
```

### 3. Install the Helm chart
``` bash
cd helm-charts
helm install todo-app ./two-tier-app
```

### 4. Access the app
- Access the app: In Kubernetes, the Flask app should be exposed via a LoadBalancer service on port 5000 (default for Flask).
- Allow inbound traffic on port 5000 (or the external port of your Flask service).


