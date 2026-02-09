# Node.js Application Deployment using GitHub Actions, Docker, Amazon ECR & ECS (Fargate)

This project demonstrates a complete **CI/CD pipeline** where a Node.js application is automatically built, containerized, pushed to **Amazon ECR**, and deployed to **Amazon ECS (Fargate)** using **GitHub Actions** — without launching any EC2 instance.

![WhatsApp Image 2026-02-09 at 12 34 41](https://github.com/user-attachments/assets/baee41a2-2ae1-4231-8db6-f0018925f3a6)


---

##  Project Overview

- Simple Node.js HTTP server
- Dockerized application
- CI/CD implemented using GitHub Actions
- Container image stored in Amazon ECR
- Application deployed on Amazon ECS (Fargate)
- No EC2 instances used (Serverless container deployment)

---

##  Tech Stack

- **Node.js**
- **Docker**
- **GitHub Actions**
- **AWS ECR (Elastic Container Registry)**
- **AWS ECS (Fargate)**
- **AWS IAM** for user access and secret key


---

##  Project Structure
```bash
.
├── .github/workflows/
│   └── aws.yml                # GitHub Actions CI/CD pipeline
├── app.js                     # Node.js application
├── Dockerfile                 # Docker configuration
├── package.json               # Node.js dependencies & scripts
├── my-task-defenation-revision1.json  # ECS task definition
└── README.md
```

---

##  Application Details

The Node.js app runs a simple HTTP server on port 3000 and returns a welcome message.
```
WELCOME TO THE WORLD OF Cloud!!!
```

---

##  Docker Configuration

The application is containerized using a lightweight Node.js Alpine image.

**Dockerfile highlights:**
- Uses node:16-alpine
- Installs dependencies
- Exposes port 3000
- Starts the application using node app.js

---

##  CI/CD Pipeline (GitHub Actions)

The CI/CD pipeline is triggered automatically on every push to the main branch.

**Pipeline Steps:**
1. Checkout source code
2. Configure AWS credentials securely using GitHub Secrets
3. Login to Amazon ECR
4. Build Docker image
5. Push Docker image to ECR
6. Update ECS task definition with new image
7. Deploy updated task to ECS service

---

##  AWS Services Used

**Amazon ECR**
- Stores Docker images securely

**Amazon ECS (Fargate)**
- Runs containers without managing EC2
- Uses awsvpc networking mode
- Security Group allows port 3000

**IAM**
- Used for secure authentication via GitHub Secrets

---

##  Security Practices

- AWS credentials stored in GitHub Secrets
- No hardcoded secrets in code
- ECS Security Group controls inbound traffic
- No EC2 instance exposed publicly

---

##  Accessing the Application

Depending on configuration:

**Via Public IP of ECS Task**
```
http://<PUBLIC-IP>:3000
```

**Via Application Load Balancer (if configured)**
```
http://<ALB-DNS-NAME>
```

---

##  Key Learning Outcomes

- Implemented CI/CD using GitHub Actions
- Dockerized a Node.js application
- Deployed containers using ECS Fargate (serverless)
- Integrated GitHub Actions with AWS
- Understood ECS networking and security groups
- No EC2 instance required for deployment

---

---

##  Author

**Samarth Funde**  
Cloud & DevOps Enthusiast 
