`jenkins-docker-flask-demo`

---

# Project Idea

A simple Flask application deployed using Docker and automated with Jenkins CI/CD pipeline.

This project demonstrates:

* GitHub integration
* Jenkins pipeline
* Docker build
* Docker container deployment
* Basic CI/CD workflow

---

# Folder Structure

```bash
jenkins-docker-flask-demo/
│
├── app.py
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
└── README.md
```

---

# 1️⃣ app.py

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Jenkins CI/CD Pipeline!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

---

# 2️⃣ requirements.txt

```txt
flask
```

---

# 3️⃣ Dockerfile

```dockerfile
FROM python:3.10

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["python", "app.py"]
```

---

# 4️⃣ Jenkinsfile

```groovy
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/SalunkeSneha/jenkins-docker-flask-demo'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-jenkins-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker stop flask-container || true'
                sh 'docker rm flask-container || true'
                sh 'docker run -d -p 5000:5000 --name flask-container flask-jenkins-app'
            }
        }

    }
}
```

Replace:

```groovy
https://github.com/SalunkeSneha?tab=repositories
```

with your actual GitHub repository URL.

Example:

```groovy
git 'https://github.com/SalunkeSneha/jenkins-docker-flask-demo.git'
```

---

# 5️⃣ README.md

Copy this directly into GitHub README.

---

# Jenkins Docker Flask CI/CD Demo

## 📌 Project Overview

This is a beginner DevOps project demonstrating a simple CI/CD pipeline using Jenkins, Docker, and Flask.

The project automates:

* Pulling code from GitHub
* Building a Docker image
* Running the application container automatically using Jenkins Pipeline

---

## 🚀 Technologies Used

* Python
* Flask
* Docker
* Jenkins
* GitHub
* Linux

---

## 📂 Project Structure

```bash
jenkins-docker-flask-demo/
│
├── app.py
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
└── README.md
```

---

## ⚙️ Jenkins Pipeline Workflow

1. Jenkins pulls code from GitHub
2. Docker image is built automatically
3. Existing container is stopped and removed
4. New container is deployed
5. Flask application runs on port 5000

---

## 🐳 Docker Commands Used

### Build Docker Image

```bash
docker build -t flask-jenkins-app .
```

### Run Container

```bash
docker run -d -p 5000:5000 --name flask-container flask-jenkins-app
```

### Check Running Containers

```bash
docker ps
```

---

## ▶️ Jenkins Pipeline Stages

* Clone Repository
* Build Docker Image
* Run Docker Container

---

## 🌐 Application Output

```text
Hello from Jenkins CI/CD Pipeline!
```

---

## 📷 Screenshots to Add

You can add:

* Jenkins pipeline success screenshot
* Docker container running screenshot
* Browser output screenshot

Create a folder named:

```bash
screenshots/
```

Example:

```markdown
![Jenkins Build](screenshots/jenkins-build.png)
```

---

## 📚 Learning Outcomes

* Basic Jenkins Pipeline
* Docker container deployment
* CI/CD workflow understanding
* GitHub integration with Jenkins
* Linux command usage

---

## 👩‍💻 Author

Sneha Salunke

---
