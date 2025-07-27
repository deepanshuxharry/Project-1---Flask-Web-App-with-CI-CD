# 01-flask-jenkins-docker-pytest

# 🚀 Flask AutoDeployer – CI/CD with Jenkins & Docker

This project demonstrates a **fully automated CI/CD pipeline** for a Flask application using **Jenkins**, **Docker**, and **Pytest**.

---

## 🛠️ Tech Stack

- **Flask** – Python web framework
- **Jenkins** – CI/CD automation
- **Docker** – Containerization
- **Pytest** – Unit testing
- **GitHub** – Source code repository
- **Linux (RHEL/CentOS)** – Jenkins host OS

---

## ⚙️ CI/CD Pipeline Overview

The Jenkins pipeline automates:

1. **Workspace cleanup**
2. **Cloning the GitHub repository**
3. **Installing dependencies**
4. **Running unit tests (Pytest)**
5. **Building a Docker image**
6. **Stopping & removing old containers**
7. **Deploying the new container**

---

## 🧪 Test Coverage

Unit tests are defined under `tests/test_app.py` to validate:

- `/` (home route)
- `/health` (health check)
- `/api/users` (users API)

---

## 🐳 Docker Details

- **Image Name:** `flaskapp-autodeployer:latest`
- **Container Name:** `flaskapp`
- **Exposed Port:** `5000`

Build & Run via:
```bash
docker build -t flaskapp-autodeployer:latest .
docker run -d -p 5000:5000 --name flaskapp flaskapp-autodeployer:latest
```

---

## 🌐 API Endpoints

| Endpoint          | Description                  |
|------------------|------------------------------|
| `/`              | Welcome message              |
| `/health`        | Health check status          |
| `/api/users`     | Sample users list            |
| `/api/metrics`   | Random system metrics        |
| `/api/logs`      | Simulated system logs        |
| `/api/config`    | App configuration values     |

---

## 📁 Project Structure

```
.
|-- Dockerfile
|-- Jenkinsfile
|-- Output_images
|-- README.md
|-- app.py
|-- config.py
|-- requirements.txt
|-- tests
|   `-- test_app.py
`-- utils
    `-- logger.py
```

---

## ✅ Jenkins Success Message

```
✅ Flask App Deployed Locally via Docker!
```


