##  Java Train Ticket Reservation System - CI/CD Pipeline using GitHub Actions, Docker & AWS

##  Project Overview

This project demonstrates a complete DevOps CI/CD pipeline for deploying a Java-based Train Ticket Reservation System using modern DevOps tools and AWS cloud services.

The application is built with Java and Maven, containerized using Docker, and automatically deployed to an AWS EC2 instance whenever code is pushed to the GitHub repository. The Docker image is stored in Amazon Elastic Container Registry (ECR), while GitHub Actions automates the entire build and deployment process. Apache2 is configured as a reverse proxy to expose the application over HTTP.

This project showcases Continuous Integration and Continuous Deployment (CI/CD) practices and serves as an end-to-end deployment solution.

---

## Architecture

```
                           Developer
                               │
                               │ Git Push
                               ▼
                     GitHub Repository (main)
                               │
                               ▼
                     GitHub Actions Workflow
                               │
          ┌────────────────────┴────────────────────┐
          │                                         │
          ▼                                         ▼
     Maven Build                             Docker Build
          │                                         │
          └────────────────────┬────────────────────┘
                               │
                               ▼
                    Amazon Elastic Container Registry
                               │
                               ▼
                     SSH Deployment to EC2
                               │
                               ▼
                      Pull Latest Docker Image
                               │
                               ▼
                    Run Docker Container (8080)
                               │
                               ▼
                    Apache2 Reverse Proxy (Port 80)
                               │
                               ▼
                           End Users
```

---

## Technologies Used

## Programming Language

- Java 17

## Build Tool

- Apache Maven

## Containerization

- Docker

## Version Control

- Git
- GitHub

## CI/CD

- GitHub Actions

## Cloud Services

- AWS EC2
- Amazon Elastic Container Registry (ECR)
- IAM

## Web Server

- Apache2 Reverse Proxy

## Operating System

- Ubuntu Server

---

## Project Structure

```
java-train-ticket-cicd-pipeline/
│
├── .github/
│   └── workflows/
│       └── cicd.yaml
│
├── src/
│
├── WebContent/
│
├── Dockerfile
│
├── pom.xml
│
├── README.md
│
├── .gitignore
│
└── screenshots/
```

---

## CI/CD Workflow

The CI/CD pipeline is fully automated using GitHub Actions.

## Step 1

Developer pushes code to the **main** branch.

↓

## Step 2

GitHub Actions automatically starts.

↓

## Step 3

Checkout project source code.

↓

## Step 4

Configure Java 17 environment.

↓

## Step 5

Build the application using Maven.

```
mvn clean package
```

↓

## Step 6

Build Docker Image.

↓

## Step 7

Authenticate with Amazon ECR.

↓

## Step 8

Push Docker Image to Amazon ECR.

↓

## Step 9

Connect to AWS EC2 using SSH.

↓

## Step 10

Pull the latest Docker image.

↓

## Step 11

Stop the existing container (if running).

↓

## Step 12

Remove the old container.

↓

## Step 13

Run the updated Docker container.

↓

## Step 14

Apache2 forwards requests to the Docker container.

↓

## Step 15

Application becomes available to users.

---

## Setup Instructions

## 1. Clone the Repository

```bash
git clone https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline.git
```

```bash
cd java-train-ticket-cicd-pipeline
```

---

## 2. Build the Project

```bash
mvn clean package
```

---

## 3. Build Docker Image

```bash
docker build -t train-ticket-app .
```

---

## 4. Run Docker Container

```bash
docker run -d \
--name train-ticket-container \
-p 8080:8080 \
train-ticket-app
```

---

## 5. Configure Apache Reverse Proxy

Enable required modules.

```bash
sudo a2enmod proxy
sudo a2enmod proxy_http
```

Update Apache Virtual Host.

```apache
ProxyPreserveHost On
ProxyPass / http://localhost:8080/
ProxyPassReverse / http://localhost:8080/
```

Restart Apache.

```bash
sudo systemctl restart apache2
```

---

## 6. Configure GitHub Secrets

Create the following repository secrets.

| Secret | Description |
|----------|------------|
| AWS_ACCESS_KEY_ID | AWS Access Key |
| AWS_SECRET_ACCESS_KEY | AWS Secret Key |
| AWS_REGION | AWS Region |
| AWS_ACCOUNT_ID | AWS Account ID |
| EC2_HOST | EC2 Public IP / Elastic IP |
| EC2_USERNAME | ubuntu |
| EC2_SSH_KEY | EC2 Private Key |

---

## 7. Push Code

```bash
git add .
git commit -m "Update project"
git push origin main
```

GitHub Actions automatically deploys the latest version.

---

## Screenshots

Add screenshots in the `screenshots` folder.

Suggested screenshots:

- GitHub Repository
- GitHub Actions Success
- Maven Build
- Docker Image
- Amazon ECR Repository
- EC2 Instance
- Docker Container Running
- Apache Reverse Proxy
- Running Application
- Project Structure

Example:

```
screenshots/
│
├── github-actions.png
├── ecr.png
├── ec2.png
├── docker.png
├── apache.png
├── application.png
```

---

## Future Improvements

- Deploy using Amazon ECS (Fargate)
- Use Application Load Balancer (ALB)
- Configure HTTPS using AWS Certificate Manager
- Infrastructure as Code using Terraform
- Monitoring with Amazon CloudWatch

---

## Author

**Khan Sadeque**


DevOps | AWS | Docker | GitHub Actions | Java | Linux | CI/CD

GitHub:
https://github.com/sadequekhan46

----------------------------------------------------