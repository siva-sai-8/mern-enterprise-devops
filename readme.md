# 🚀 Enterprise-Grade MERN Stack DevOps Pipeline on AWS

This project implements a complete enterprise-level DevOps architecture for a MERN stack application. It includes CI/CD, containerization, security scanning, infrastructure as code, monitoring, secrets management, and automated deployments using modern tools and AWS services.

> 📝 **Note**: The application code used in this project is based on [RishiBakshii/mern-ecommerce](https://github.com/RishiBakshii/mern-ecommerce), licensed under the MIT License. This repo focuses on the DevOps pipeline built around the app.

---

## 📁 Tech Stack

- Frontend: React  
- Backend: Node.js + Express  
- Database: MongoDB (Atlas / self-hosted)  
- DevOps Tools: GitHub Actions, Docker, Terraform, SonarQube, Trivy, ECR, EC2/ECS, NGINX, Prometheus, Grafana, AWS Secrets Manager, CloudWatch, Route 53, Certbot/ACM

---

## 🗂️ Folder Structure

mern-enterprise-devops/
├── frontend/ # React app
├── backend/ # Express app
├── .github/workflows/ # GitHub Actions CI/CD pipelines
├── terraform/ # Infrastructure as Code (AWS setup)
├── docker-compose.yml # Local and deployment config
├── deploy.sh # Deployment script
├── README.md




---

## 🛠️ DevOps Pipeline Stages

### ✅ 1. GitHub Repository & Branching Strategy
- Branches: `main`, `develop`, `release/*`, `hotfix/*`
- Pull Requests: Protected branches with mandatory reviews and checks
- Actions: CI/CD triggered on push & PR to `main` and `develop`

### ✅ 2. Code Quality & Security
- 🔍 SonarQube: Static code analysis for bugs, vulnerabilities, code smells
- 🛡️ Trivy: Scans Docker images for vulnerabilities
- 📦 Dependabot: Automatically updates vulnerable dependencies

### ✅ 3. Build & Test Automation (CI)
Via GitHub Actions:
- Run unit tests (Jest, Mocha)
- Lint checks (eslint)
- Code quality (SonarQube)
- Build React frontend and Node backend

### ✅ 4. Dockerization
- Dockerfile for both frontend and backend
- Multi-container setup via docker-compose
- `.dockerignore` for clean images

### ✅ 5. Container Registry
- AWS ECR used for image storage
- Tags used: `latest`, `dev`, `v1.0.0`, `release-*`, etc.

### ✅ 6. Infrastructure as Code (IaC)
- Terraform scripts to provision:
  - VPC, EC2, Security Groups
  - ECR, IAM Roles, Secrets Manager
  - RDS/MongoDB (if not Atlas)
- Stored in `terraform/` folder
- Executed via GitHub Actions or manually

### ✅ 7. Secrets Management
- 🔐 AWS Secrets Manager or Parameter Store
- Credentials like DB URIs, API Keys injected securely at runtime
- Never committed in GitHub or `.env` files

### ✅ 8. CI/CD Deployment
- Fully automated on push to `main` or `develop`
- Steps:
  1. Pull source
  2. Run tests & SonarQube
  3. Build Docker images
  4. Push to ECR
  5. Trigger `deploy.sh` on EC2 via SSH or SSM

### ✅ 9. Deployment Strategy
- EC2: Docker Compose + NGINX + Certbot SSL
- ECS Fargate: For serverless scaling (optional)
- Blue/Green or Rolling deployments

### ✅ 10. Monitoring & Logging
- Prometheus + Grafana → Metrics
- Loki or ELK Stack → Centralized Logging
- Alerts via Slack, Email, PagerDuty (optional)

### ✅ 11. Domains & SSL
- Route 53: DNS management
- NGINX + Certbot (EC2) OR ACM (ECS)
- Auto-renewal with Certbot or managed via ACM

### ✅ 12. IAM & Security
- IAM roles with least privilege
- GitHub Actions → OIDC authentication (no static keys)
- Enforced access policies on S3, ECR, EC2

### ✅ 13. Backups & Rollbacks
- RDS snapshots, AMIs for EC2
- Rollback via Docker image versioning (tagged releases)
- Manual or automated restore supported

### ✅ 14. Cost Optimization
- Spot Instances or AutoStop EC2 for dev
- Savings Plans for long-term
- Budget Alerts via CloudWatch and AWS Budgets

### ✅ 15. Documentation
Stored in `docs/` or Confluence/Notion:
- Infrastructure Diagrams
- CI/CD Flowcharts
- Rollback Procedures
- Secrets & IAM Policy Matrix
- Onboarding Docs

---

## ⚙️ Optional (But Advanced) Tools

| Tool             | Purpose                          |
|------------------|----------------------------------|
| Ansible          | Server provisioning              |
| ArgoCD           | GitOps-based K8s deployments     |
| Nexus            | Internal artifact storage        |
| HashiCorp Vault  | Advanced secrets management      |
| K9s              | TUI for managing Kubernetes      |

---


## 🔐 Contributors

- 🛠️ Frontend & Backend App originally built by [RishiBakshii](https://github.com/RishiBakshii) under the MIT License.
- 🚀 DevOps Infrastructure, CI/CD Pipeline, and Cloud Automation by **Naga Siva Sai** — aspiring DevOps Engineer, focused on cloud-native architecture & automation.


## 📄 License

This project is licensed under the **MIT License**.  
Base application sourced from [RishiBakshii/mern-ecommerce](https://github.com/RishiBakshii/mern-ecommerce) and reused in compliance with its MIT license.
