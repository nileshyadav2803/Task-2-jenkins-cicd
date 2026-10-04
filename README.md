🚀 Jenkins CI/CD Pipeline with Docker

A simple DevOps project demonstrating how Jenkins can automate the build, test, and deployment process of a Dockerized web application.


---

📌 Project Objective

The objective of this project is to create a basic CI/CD pipeline using Jenkins and Docker.

The pipeline automatically:

Checks out the project from GitHub

Builds the Docker image

Runs the test stage

Deploys the application using Docker



---

🛠️ Technologies Used

Technology	Purpose

Jenkins	CI/CD automation
Docker	Containerization and deployment
Git	Version control
GitHub	Source code repository
Nginx	Web server
HTML	Web application



---

🔄 CI/CD Pipeline Flow

Developer
    ↓
GitHub Repository
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
Web Application


---

📁 Project Structure

Task-2-jenkins-cicd/
│
├── Dockerfile
├── Jenkinsfile
├── index.html
└── README.md


---

🐳 Docker Configuration

The application is packaged into a Docker image using an Nginx Alpine base image.

The Dockerfile:

Uses Nginx Alpine

Copies index.html into the Nginx web directory

Creates a lightweight containerized web application



---

⚙️ Jenkins Pipeline

The pipeline is defined using a Jenkinsfile stored in the GitHub repository.

1. Checkout SCM

Jenkins retrieves the latest source code from the GitHub repository.

2. Build

Docker builds the application image from the Dockerfile.

3. Test

The pipeline executes the configured test/verification step.

4. Deploy

The Docker container is started to deploy the application.


---

🔔 Automated Trigger

Jenkins is configured with Poll SCM.

H/1 * * * *

This allows Jenkins to periodically check the GitHub repository for source-code changes.

When a new commit is detected, Jenkins can automatically start a new pipeline build.


---

▶️ Running the Application

After successful deployment, the application can be accessed locally at:

http://localhost:8080

Expected output:

Jenkins CI/CD Pipeline

Deployment successful!


---

✅ Pipeline Verification

The Jenkins pipeline was successfully executed with the following stages:

✓ Checkout SCM
✓ Build
✓ Test
✓ Deploy

The Jenkins build completed with:

Finished: SUCCESS

The deployed web application was also verified through the browser.


---

📸 Project Evidence

The project includes verification of:

Jenkins pipeline execution

Successful build

Pipeline stages

Docker deployment

Running web application

GitHub repository containing the Jenkinsfile



---

🎯 Learning Outcomes

Through this project, I learned:

Basics of CI/CD

Jenkins Pipeline

Jenkinsfile and Pipeline as Code

Docker image building

Docker container deployment

GitHub integration with Jenkins

SCM polling

Automated build and deployment workflow



---

👨‍💻 Author

Nilesh Yadav

BCA Graduate | Aspiring Cloud / DevOps Engineer

GitHub:
https://github.com/nileshyadav2803