##  Java Train Ticket Reservation System - CI/CD Pipeline using GitHub Actions, Docker & AWS

##  Project Overview

This project demonstrates a complete DevOps CI/CD pipeline for deploying a Java-based Train Ticket Reservation System using modern DevOps tools and AWS cloud services.

The application is built with Java and Maven, containerized using Docker, and automatically deployed to an AWS EC2 instance whenever code is pushed to the GitHub repository. The Docker image is stored in Amazon Elastic Container Registry (ECR), while GitHub Actions automates the entire build and deployment process. Apache2 is configured as a reverse proxy to expose the application over HTTP.

This project showcases Continuous Integration and Continuous Deployment (CI/CD) practices and serves as an end-to-end deployment solution.
---
## Architecture
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/09f5bbc5e367fb954c18cabce6389041e35d1a8c/Screenshots/project-structure.png)
```

## Technologies Used
- Java 17
- Apache Maven
- Docker
- Git
- GitHub
- GitHub Actions
- AWS EC2
- Amazon Elastic Container Registry (ECR)
- IAM
- Apache2 Reverse Proxy
- Ubuntu Server
---
## Project Structure

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
mvn clean package
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
```
## Setup Instructions
## 1. Clone the Repository
git clone https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline.git
cd java-train-ticket-cicd-pipeline
## 2. Build the Project
mvn clean package
## 3. Build Docker Image
docker build -t train-ticket-app .
## 4. Run Docker Container
docker run -d \
--name train-ticket-container \
-p 8080:8080 \
train-ticket-app
## 5. Configure Apache Reverse Proxy
Enable required modules
```
sudo a2enmod proxy
sudo a2enmod proxy_http
```
Update Apache Virtual Host.

apache
ProxyPreserveHost On
ProxyPass / http://localhost:8080/
ProxyPassReverse / http://localhost:8080/
```
Restart Apache.
sudo systemctl restart apache2
```
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
---
git add .
git commit -m "Update project"
git push origin main
GitHub Actions automatically deploys the latest version.

## Screenshots
- GitHub Repository
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/9f52553c4164493e6da0b927e74ea0e11d036478/Screenshots/GIthub-repository.png)

- GitHub Actions Success
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/main/Screenshots/Github-secrets.png)

- Maven Build
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/main/Screenshots/maven%20build.png)

- Docker Image
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/main/Screenshots/docker-images.png)

- Amazon ECR Repository
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/b2eac39df462745f1084e3bac5014a107f7c3b51/Screenshots/ecr-latest-image.png)

- EC2 Instance
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/b2eac39df462745f1084e3bac5014a107f7c3b51/Screenshots/ec2-instance.png)

- security-group
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/b90787819ac10a2a022ec653b606b51c3d515697/Screenshots/security-group.png)
-Elastic ip
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/main/Screenshots/elastic-ip.png)

- IAM user
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/b90787819ac10a2a022ec653b606b51c3d515697/Screenshots/IAM-user.png)

- Docker Container Running
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/8780fc6f0e64f6fce21612f7e2fea8d8b212d09e/Screenshots/docker%20container%20running.png)

- Apache Reverse Proxy
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/main/Screenshots/Apache-reverse-proxy.png)

- cicd pipline
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/b90787819ac10a2a022ec653b606b51c3d515697/Screenshots/github-action-cicd.png)

-Docker Container Running
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/b2eac39df462745f1084e3bac5014a107f7c3b51/Screenshots/Docker-container-deployed.png)

- Running Application
![image alt](https://github.com/sadequekhan46/java-train-ticket-cicd-pipeline/blob/b90787819ac10a2a022ec653b606b51c3d515697/Screenshots/54.152.221.119.png)


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
----------------------------------------------------