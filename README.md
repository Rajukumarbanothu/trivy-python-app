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
