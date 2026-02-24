# 🚀 MEAN Stack CRUD Application (DevOps Integrated)

A full-stack MEAN (MongoDB, Express, Angular, Node.js) CRUD application fully containerized and deployed using modern DevOps practices.

---

## 📌 Project Overview

This project is:

- ✅ Containerized using Docker  
- ✅ Orchestrated using Docker Compose  
- ✅ Deployed on AWS EC2 (Ubuntu 22.04)  
- ✅ Served via Nginx Reverse Proxy  
- ✅ Integrated with GitHub Actions CI/CD  
- ✅ Automatically deployed on every push  

The application performs complete **Create, Read, Update, Delete (CRUD)** operations.

---

## 🏗️ Architecture Overview

```
User (Browser)
        ↓
Nginx (Frontend Container - Port 80)
        ↓
Node.js + Express Backend (Port 8080)
        ↓
MongoDB (Database Container)
```

---

## 🔄 CI/CD Workflow

```
git push
   ↓
GitHub Actions
   ↓
Build Docker Images
   ↓
Push to Docker Hub
   ↓
SSH to AWS EC2
   ↓
docker-compose pull
   ↓
docker-compose up -d
   ↓
Application Updated Automatically
```

---

## 🛠️ Tech Stack

### 📌 Frontend
- Angular 15
- TypeScript
- Nginx (Production Serving)

### 📌 Backend
- Node.js
- Express.js
- Mongoose

### 📌 Database
- MongoDB (Docker container)

### 📌 DevOps
- Docker (Multi-stage builds)
- Docker Compose
- AWS EC2 (Ubuntu 22.04)
- GitHub Actions
- Docker Hub

---

# ⚙️ Setup & Deployment Instructions

---

## 1️⃣ Local Setup (Docker-Based)

### 🔹 Prerequisites
- Docker installed  
- Docker Compose installed  
- Git installed  

### 🔹 Build and Run Containers

```bash
docker-compose up --build
```

### 🔹 Access Application
```
http://localhost
```

---

## 2️⃣ AWS EC2 Deployment

### 🔹 Step 1: Launch EC2 Instance
- OS: Ubuntu 22.04
- Instance type: t2.micro
- Open inbound ports:
  - 22 (SSH)
  - 80 (HTTP)

### 🔹 Step 2: Connect to EC2

```bash
ssh ubuntu@your-ec2-public-ip
```

### 🔹 Step 3: Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
```

### 🔹 Step 4: Install Docker Compose

```bash
sudo apt install docker-compose -y
```

### 🔹 Step 5: Create Project Directory

```bash
mkdir mean-app
cd mean-app
```

### 🔹 Step 6: Create docker-compose.yml

(Add your docker-compose configuration here)

### 🔹 Step 7: Deploy Application

```bash
docker-compose up -d
```

---

## 3️⃣ CI/CD Pipeline Setup (GitHub Actions)

### 🔹 Step 1: Add GitHub Secrets

Add the following repository secrets:

- `DOCKER_USERNAME`
- `DOCKER_PASSWORD` (Docker Hub Access Token)
- `AWS_SSH_KEY`
- `AWS_HOST`
- `AWS_USER`

---

### 🔹 Step 2: Add GitHub Actions Workflow

Pipeline performs:

- Docker login  
- Build backend image  
- Build frontend image  
- Push images to Docker Hub  
- SSH into AWS  
- Pull latest images  
- Restart containers  

---

## 🚀 Automatic Deployment Process

On every `git push`:

- Images are rebuilt  
- Images are pushed to Docker Hub  
- AWS server pulls latest images  
- Containers restart  
- Application updates live  
- No manual deployment required  

---

## 🔁 Final Deployment Flow

```
Code Change
     ↓
git push
     ↓
GitHub Actions
     ↓
Docker Hub
     ↓
AWS EC2 Auto Deploy
     ↓
Live Application Updated
```

