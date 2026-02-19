# 🛡️ Trivy Python App – DevSecOps Container Security Implementation

## 📖 Project Overview

This project demonstrates how to integrate **container security scanning** into a DevSecOps workflow using:

- Python Flask Application
- Docker Containerization
- Trivy Vulnerability Scanner
- GitHub Actions CI/CD Pipeline

The goal is to automatically detect vulnerabilities in Docker images and block insecure deployments.

---

## 🏗️ Project Architecture

Developer → Build Docker Image → Trivy Scan →  
Fail if HIGH/CRITICAL → Fix → Rebuild → Deploy

This simulates a real-world DevSecOps security gate.

---

## 🚀 Step 1: Python Application

### app.py

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def home():
    return "Hello DevSecOps!"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
requirements.txt
flask


Run locally:

python app.py
##🐳 Step 2: Dockerize the Application
Dockerfile
FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install --no-cache-dir -r requirements.txt
CMD ["python", "app.py"]
Build image:

docker build -t trivy-python-app:v1 .


Run container:

docker run -p 5000:5000 trivy-python-app:v1

##🔍 Step 3: Scan Docker Image Using Trivy (Manual Scan)
Scan image:

trivy image trivy-python-app:v1


Generate JSON report:

trivy image -f json -o trivy-report.json trivy-python-app:v1


Generate table report:

trivy image -f table -o trivy-report.txt trivy-python-app:v1

