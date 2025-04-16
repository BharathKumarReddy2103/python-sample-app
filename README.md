# 🚀 Python Sample App - DevOps CI/CD Pipeline

Welcome to the **Python Sample App**, a minimal Flask application packaged with a complete DevOps pipeline. This project demonstrates how to:

- Build a Python web app using Flask
- Containerize the app with Docker
- Automate builds and Docker image pushes via **GitHub Actions**
- Deploy to **Kubernetes** locally using **Minikube**
- Use NodePort service for local browser access

> 👨‍💻 Created and maintained by [Bharath Kumar Reddy](https://github.com/BharathKumarReddy2103)

---

## 📂 Project Structure

```
python-sample-app/
├── app.py                  # Flask web app
├── requirements.txt        # Python dependencies
├── Dockerfile              # Container setup
├── README.md               # Project documentation
├── .github/
│   └── workflows/
│       └── docker-build.yml  # GitHub Actions pipeline
└── k8s/
    ├── deployment.yaml     # Kubernetes Deployment
    └── service.yaml        # Kubernetes Service (NodePort)
```

---

## ⚙️ CI/CD with GitHub Actions

This repo includes a GitHub Actions workflow that:

- Triggers on push to the `main` branch
- Builds the Docker image using your `Dockerfile`
- Pushes the image to DockerHub (`nbkumar2103/python-sample-app:latest`)

📁 File: `.github/workflows/docker-build.yml`

> Secrets required:
- `DOCKER_USERNAME`
- `DOCKER_PASSWORD`

---

## 🐳 Docker Commands (Local Build)

```bash
# Build image
docker build -t nbkumar2103/python-sample-app .

# Run container
docker run -p 5000:5000 nbkumar2103/python-sample-app

# Test locally
curl http://localhost:5000
```

---

## ☸️ Kubernetes Deployment (Minikube)

### 🔧 Prerequisites
- Docker
- Minikube
- kubectl

### 📦 Steps

```bash
# Start Minikube
minikube start

# Create namespace
kubectl create namespace demo

# Deploy to Kubernetes
kubectl apply -f k8s/deployment.yaml -n demo
kubectl apply -f k8s/service.yaml -n demo

# Get service URL
minikube service python-sample-service -n demo --url
```

Visit the URL in your browser. You should see:

```
Hello 👋 from Bharath Kumar Reddy’s Python App!
```

---

## 🔗 Endpoints

| Endpoint      | Description               |
|---------------|---------------------------|
| `/`           | Home Page                 |
| `/status`     | Health Check (JSON)       |

---

## 📦 DockerHub

- 🔗 [View on DockerHub](https://hub.docker.com/r/nbkumar2103/python-sample-app)

---

## 📈 DevOps Tech Stack

- Python 3.9 + Flask
- Docker
- GitHub Actions
- Kubernetes (Minikube)
- CI/CD Workflow Automation

---

## 🧑‍💻 Author

**Bharath Kumar Reddy**  
Senior DevOps & DataOps Engineer  
[GitHub Profile](https://github.com/BharathKumarReddy2103)

---

## ⭐ Contribute

Want to improve this pipeline? Fork the repo, create a feature branch, and submit a pull request.

---

## 📜 License

This project is licensed under the MIT License.
