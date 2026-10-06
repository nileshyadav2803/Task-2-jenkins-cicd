# 🚀 Task 2 — Jenkins CI/CD Pipeline with Docker

[![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-D24939?logo=jenkins\&logoColor=white)](https://www.jenkins.io/) [![Docker](https://img.shields.io/badge/Docker-Containerization-2496ED?logo=docker\&logoColor=white)](https://www.docker.com/) [![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?logo=github\&logoColor=white)](https://github.com/) [![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-009639?logo=nginx\&logoColor=white)](https://nginx.org/) [![Status](https://img.shields.io/badge/Status-Completed-success)]

> A practical DevOps internship project demonstrating how **Jenkins and Docker** can be used to automate the build, test, and deployment of a containerized web application.

---

## 📌 Table of Contents

* 🎯 Project Overview
* 🛠️ Tools Used
* 📁 Project Structure
* 🏗️ Project Architecture
* 🔄 CI/CD Workflow
* ⚙️ Jenkins Pipeline
* 🐳 Docker Configuration
* 🔔 SCM Trigger
* 🌐 Application Deployment
* 📸 Evidence
* 🎓 What I Learned
* ⚠️ Issues Encountered
* 🧠 Key Commands
* ✅ Project Status
* 🏁 Conclusion

---

## 🎯 Project Overview

The objective of this project was to create a basic **Jenkins CI/CD pipeline** for a Dockerized web application.

The project demonstrates how Jenkins can automate the main stages of a CI/CD workflow:

* Checkout source code from GitHub
* Build a Docker image
* Verify the Docker image
* Deploy the application using Docker
* Configure SCM polling for repository changes
* Verify the deployed application through a browser

The project follows the workflow:

```text
GitHub
   ↓
Jenkins
   ↓
Checkout SCM
   ↓
Build
   ↓
Test
   ↓
Deploy
   ↓
Docker Container
   ↓
Nginx Web Application
```

---

## 🛠️ Tools Used

| Tool        | Purpose                         |
| ----------- | ------------------------------- |
| **Jenkins** | CI/CD automation                |
| **Docker**  | Containerization and deployment |
| **Git**     | Version control                 |
| **GitHub**  | Remote repository               |
| **Nginx**   | Web server                      |
| **HTML**    | Web application                 |
| **VS Code** | Development environment         |
| **Windows** | Local development environment   |

---

## 📁 Project Structure

```text
Task-2-jenkins-cicd/
│
├── 📄 Dockerfile
├── 📄 Jenkinsfile
├── 📄 index.html
├── 📄 README.md
│
└── 📂 screenshots/
    ├── 📸 GitHub Repository
    ├── 📸 Jenkins Pipeline
    ├── 📸 Pipeline Stages
    ├── 📸 Application Deployment
    └── 📸 SCM Trigger
```

### File Purpose

| File / Folder  | Purpose                            |
| -------------- | ---------------------------------- |
| `Dockerfile`   | Defines the Docker image           |
| `Jenkinsfile`  | Defines the Jenkins CI/CD pipeline |
| `index.html`   | Simple web application             |
| `README.md`    | Project documentation              |
| `screenshots/` | Evidence of project execution      |

---

## 🏗️ Project Architecture

```text
                ┌──────────────────┐
                │      GitHub      │
                │ Source Repository│
                └────────┬─────────┘
                         │
                         ▼
                ┌──────────────────┐
                │     Jenkins      │
                │   CI/CD Server   │
                └────────┬─────────┘
                         │
              ┌──────────┴──────────┐
              │                     │
              ▼                     ▼
        Checkout SCM             Jenkinsfile
                                    │
                                    ▼
                                  Build
                                    │
                                    ▼
                                  Test
                                    │
                                    ▼
                                 Deploy
                                    │
                                    ▼
                            ┌────────────────┐
                            │ Docker         │
                            │ Container      │
                            │     Nginx      │
                            └───────┬────────┘
                                    │
                                    ▼
                           localhost:8080
```

---

## 🔄 CI/CD Workflow

The project follows this workflow:

### 1. Source Code

The application source code is maintained in a GitHub repository.

### 2. Jenkins Checkout

Jenkins retrieves the project source code from the GitHub `main` branch.

### 3. Build

Jenkins builds the Docker image using the project's `Dockerfile`.

### 4. Test

Jenkins verifies that the Docker image was successfully created.

### 5. Deploy

Jenkins starts a Docker container using the generated image.

### 6. Verification

The deployed web application is accessed through:

```text
http://localhost:8080
```

---

## ⚙️ Jenkins Pipeline

The pipeline is defined using a `Jenkinsfile`.

The project uses a **Declarative Jenkins Pipeline**.

### Pipeline Stages

```text
Checkout SCM
     ↓
Build
     ↓
Test
     ↓
Deploy
```

### Checkout SCM

Jenkins checks out the source code from GitHub.

### Build

The Docker image is created using:

```bash
docker build -t task-2-jenkins-cicd .
```

### Test

The generated Docker image is verified using:

```bash
docker image inspect task-2-jenkins-cicd
```

### Deploy

The application is deployed using:

```bash
docker run -d --name task2-app -p 8080:80 task-2-jenkins-cicd
```

---

## 🐳 Docker Configuration

The project uses **Nginx Alpine** as the base image.

### Dockerfile

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

### Docker Configuration Explained

| Configuration       | Purpose                                  |
| ------------------- | ---------------------------------------- |
| `FROM nginx:alpine` | Uses lightweight Nginx image             |
| `COPY index.html`   | Copies the web page into Nginx           |
| Port `80`           | Nginx container HTTP port                |
| Port `8080`         | Host port used to access the application |

The application is therefore accessed using:

```text
http://localhost:8080
```

---

## 🔔 SCM Trigger

Jenkins was configured with **Poll SCM** to periodically check the GitHub repository for changes.

Configured schedule:

```text
H/1 * * * *
```

The purpose of SCM polling is to allow Jenkins to check the repository for new commits and trigger a pipeline build when a change is detected.

---

## 🌐 Application Deployment

After the Jenkins pipeline successfully completed the deployment stage, the application was available at:

```text
http://localhost:8080
```

### Application Output

```text
Jenkins CI/CD Pipeline

Deployment successful!
```

The application was served by **Nginx inside a Docker container**.

---

## 📸 Evidence

The `screenshots/` directory contains evidence of the completed project.

| Evidence                 | Description                                 |
| ------------------------ | ------------------------------------------- |
| `GitHub Repository`      | Project files available on GitHub           |
| `Jenkins Pipeline`       | Jenkins job configuration and execution     |
| `Pipeline Stages`        | Checkout SCM, Build, Test and Deploy stages |
| `Application Deployment` | Successfully deployed web application       |
| `SCM Trigger`            | Poll SCM configuration                      |

### Successful Jenkins Pipeline

The Jenkins pipeline completed with:

```text
Finished: SUCCESS
```

The pipeline stages were successfully executed:

```text
✓ Checkout SCM
✓ Build
✓ Test
✓ Deploy
```

---

## 🎓 What I Learned

Through this project, I learned and practiced:

* Jenkins installation and basic configuration
* Jenkins Pipeline
* Declarative Jenkinsfile
* CI/CD concepts
* GitHub integration with Jenkins
* SCM polling
* Docker image creation
* Docker container deployment
* Docker port mapping
* Nginx containerization
* Pipeline stages
* Build and deployment automation
* Basic CI/CD troubleshooting

---

## ⚠️ Issues Encountered

### 1. Jenkins Java Requirement

Jenkins required a compatible Java environment, so Java 21 was configured for running Jenkins.

### 2. Docker Image Build

The Docker image was successfully created using:

```bash
docker build -t task-2-jenkins-cicd .
```

### 3. Docker Port Mapping

The application used the following port mapping:

```text
8080:80
```

This means:

```text
Host Port 8080 → Container Port 80
```

### 4. Git Push Connection Issue

During the project, a Git push encountered a temporary connection reset:

```text
error: RPC failed
curl 35 Recv failure: Connection was reset
fatal: the remote end hung up unexpectedly
```

The repository state was subsequently verified and the project files were successfully synchronized with GitHub.

---

## 🧠 Key Commands

### Git Commands

```bash
git status

git add .

git commit -m "message"

git push origin main
```

### Docker Commands

```bash
docker --version

docker build -t task-2-jenkins-cicd .

docker image inspect task-2-jenkins-cicd

docker run -d --name task2-app -p 8080:80 task-2-jenkins-cicd

docker ps

docker ps -a
```

### Jenkins

Jenkins was started locally using:

```bash
java -jar jenkins.war --httpPort=8081
```

Jenkins dashboard:

```text
http://localhost:8081
```

Application:

```text
http://localhost:8080
```

---

## ✅ Project Status

| Requirement               | Status     |
| ------------------------- | ---------- |
| Jenkins setup             | ✅ Complete |
| Docker setup              | ✅ Complete |
| GitHub repository         | ✅ Complete |
| Dockerfile                | ✅ Complete |
| Jenkinsfile               | ✅ Complete |
| Jenkins Pipeline          | ✅ Complete |
| Checkout SCM              | ✅ Complete |
| Build stage               | ✅ Complete |
| Test stage                | ✅ Complete |
| Deploy stage              | ✅ Complete |
| SCM Polling configuration | ✅ Complete |
| Docker deployment         | ✅ Complete |
| Browser verification      | ✅ Complete |
| README.md                 | ✅ Complete |
| Evidence screenshots      | ✅ Added    |
| Final verification        | ✅ Complete |

---

## 🏁 Conclusion

This project demonstrates a practical **Jenkins + Docker CI/CD workflow** suitable for a DevOps environment.

The project successfully connects source-code management with Jenkins automation and Docker deployment:

```text
GitHub
   ↓
Jenkins
   ↓
Checkout SCM
   ↓
Build
   ↓
Test
   ↓
Deploy
   ↓
Docker Container
   ↓
Nginx
   ↓
Web Application
```

The project provided hands-on experience with **Jenkins Pipeline, Jenkinsfile, Docker containerization, GitHub integration, SCM polling, automated build, and application deployment**.

---

## 🚀 Final Project

**Task 2 — Jenkins CI/CD Pipeline with Docker**

**Status:** `Completed`

---

**GitHub Repository:**

`https://github.com/nileshyadav2803/Task-2-jenkins-cicd`
