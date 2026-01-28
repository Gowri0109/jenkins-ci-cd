#  Jenkins CI/CD Pipeline for Python Flask Application

This repository demonstrates a real-time CI/CD pipeline using Jenkins to automate the build, containerization, and deployment of a Python Flask application using Docker, Docker Hub, and AWS EC2.
The pipeline is event-driven and triggered automatically using GitHub Webhooks.

---

## 📌 Project Objective

To design and implement an end-to-end Jenkins CI/CD pipeline that:

- Automatically triggers on every GitHub code push

 - Builds a Docker image for a Flask application

- Pushes the image to Docker Hub

- Deploys the latest version to an AWS EC2 instance

---

##  Tech Stack

- Python – Flask Framework

- Jenkins – CI/CD Automation

- Docker – Containerization

- Docker Hub – Image Registry

- GitHub – Source Code Management

- GitHub Webhooks – Real-time pipeline triggering

- AWS EC2 – Application Hosting

---

##  CI/CD Workflow

1. Developer pushes code to GitHub

2. GitHub Webhook sends an HTTP POST request to Jenkins

3. Jenkins pipeline is triggered automatically

4. Docker image is built from the application source

5. Image is pushed to Docker Hub

6. Application is deployed as a container on AWS EC2

7. Flask app is accessible via public IP

---
##  Architecture Diagram
```
                ┌────────────────────┐
                │     Developer      │
                │   (git push)       │
                └─────────┬──────────┘
                          │
                          ▼
                ┌────────────────────┐
                │      GitHub        │
                │ (Webhook Enabled)  │
                └─────────┬──────────┘
                          │  HTTP POST
                          ▼
                ┌────────────────────┐
                │      Jenkins        │
                │  CI/CD Pipeline    │
                │ (Running on EC2)   │
                └─────────┬──────────┘
                          │
          ┌───────────────┼─────────────────┐
          ▼               ▼                 ▼
┌────────────────┐ ┌────────────────┐ ┌────────────────────┐
│ Build Image    │ │ Push to Hub    │ │ Deploy Container   │
│ (Docker)       │ │ (Docker Hub)   │ │ (AWS EC2)          │
└────────────────┘ └────────────────┘ └────────────────────┘
                          │
                          ▼
                ┌────────────────────┐
                │    Flask App       │
                │  Port: 5000        │
                └────────────────────┘
                          │
                          ▼
                ┌────────────────────┐
                │     End Users      │
                │ http://EC2-IP:5000 │
                └────────────────────┘
```
---

##  Jenkins Pipeline Stages

The CI/CD pipeline is written using a Declarative Jenkinsfile and consists of the following stages:

1. Checkout SCM – Pulls source code from GitHub

2. Build Docker Image – Builds the Flask application image

3. Push to Docker Hub – Pushes the image to Docker Hub registry

4. Deploy – Stops old container and runs the latest image

5. Post Actions – Confirms pipeline execution status

---

##  Webhook Configuration

GitHub Webhook configured with Jenkins endpoint:

```
http://<JENKINS_EC2_PUBLIC_IP>:8080/github-webhook/
```


Jenkins job configured with:

- GitHub hook trigger for GITScm polling

Enables real-time, event-driven pipeline execution

Eliminates manual builds and SCM polling

---

##  Docker Hub Repository

Docker images are pushed to:

```
gowrisuresh0109/flask-project
```
---

## 📂 Project Structure
```
.
├── app.py
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
└── README.md
```

---
##  Application Access

Once deployed successfully, the Flask application is accessible at:

```
http://<EC2_PUBLIC_IP>:5000
```

Output:
```
Flask App is Running Successfully 
```

---
##  Key Features

Real-time CI/CD using GitHub Webhooks

Fully automated Docker build and deployment

Secure credential management in Jenkins

Declarative Jenkins pipeline

Production-style DevOps workflow

---

## 📚 Key Learnings

- Jenkins pipeline automation with Webhooks

- Docker image lifecycle management

- CI/CD deployment strategies on AWS EC2

- Event-driven DevOps architecture

---

##  Future Enhancements

- Add automated test stage

- Implement Docker Compose

- Deploy using Kubernetes

 - Add Nginx reverse proxy

 - Enable HTTPS using SSL

----

##  Author

Gowri Suresh
DevOps & Cloud Enthusiast
GitHub: https://github.com/Gowri0109




