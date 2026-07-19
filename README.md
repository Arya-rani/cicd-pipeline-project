# CI/CD Kubernetes Pipeline Project

A Flask web application containerized with Docker and deployed to a Kubernetes cluster (Amazon EKS) on AWS, with automated CI/CD using GitHub Actions.

## 🧱 Tech Stack

- **Application:** Python, Flask
- **Containerization:** Docker
- **Container Registry:** Amazon ECR (Elastic Container Registry)
- **Orchestration:** Kubernetes (Amazon EKS)
- **CI/CD:** GitHub Actions
- **Cloud Provider:** AWS (IAM, ECR, EKS, EC2, Elastic Load Balancer)

## 📐 Architecture

## 🚀 What the App Does

A minimal Flask API with two endpoints:
- `/` — returns a JSON welcome message
- `/health` — returns a health check response (`{"status": "healthy"}`), used to confirm the app is running correctly inside Kubernetes

## 🖥️ Running Locally

```bash
git clone https://github.com/Arya-rani/cicd-pipeline-project.git
cd cicd-pipeline-project

python3 -m venv venv
source venv/bin/activate

pip install -r requirements.txt

python app.py
```
Visit `http://127.0.0.1:5050` in your browser.

## 🐳 Running with Docker

```bash
docker build -t flask-cicd-app .
docker run -p 5050:5050 flask-cicd-app
```

## ☸️ Deploying to Kubernetes (AWS EKS)

1. Push the Docker image to Amazon ECR
2. Apply the Kubernetes manifests:
```bash
   kubectl apply -f deployment.yaml
   kubectl apply -f service.yaml
```
3. Get the public URL:
```bash
   kubectl get service flask-cicd-service
```

## 🔄 CI/CD Pipeline

On every push to the `main` branch, GitHub Actions automatically:
1. Builds a new Docker image
2. Pushes it to Amazon ECR
3. Deploys the updated image to the EKS cluster

## 📸 Screenshots

*(Add your screenshots here — app running locally, app running in Docker, live app via LoadBalancer URL, GitHub Actions pipeline run)*

## 🔮 Future Improvements

- Add Prometheus + Grafana for cluster monitoring
- Add Horizontal Pod Autoscaling (HPA)
- Migrate manifests to a Helm chart
- Add HTTPS via an SSL certificate and custom domain

## 📝 Notes

This project was built as a hands-on learning exercise covering the full DevOps lifecycle: containerization, cloud infrastructure, container orchestration, and CI/CD automation.
