# 🔧 AWS Infrastructure Automation using Ansible, Jenkins, and GitHub

## 📘 Project Overview

This project demonstrates a complete DevOps pipeline to provision and deploy a multi-tier web application on AWS using **Ansible**, **Jenkins**, and **GitHub**. It automates infrastructure provisioning, application deployment, and integrates CI/CD workflows using Infrastructure as Code (IaC) principles.

---

## 🎯 Objectives

- Provision EC2 instances and RDS on AWS using Ansible.
- Deploy a web app stack: Nginx (frontend), Flask (backend), MySQL (RDS).
- Create Ansible roles for modular configuration management.
- Set up Jenkins for continuous integration and deployment.
- Integrate GitHub for source control and webhooks.
- Use dynamic inventory to target AWS instances.
- (Optional) Enable monitoring with Prometheus and alerts via Slack.

---

## 🧱 Architecture

```text
             ┌─────────────┐
             │  GitHub Repo│
             └────┬────────┘
                  │
                  ▼
           ┌────────────┐
           │ Jenkins CI │ ◄──── Webhook
           └────┬───────┘
                │
         ┌──────▼────────┐
         │ Ansible Control│
         └───┬────┬───────┘
             │    │
     ┌───────▼─┐ ┌▼─────────┐
     │ Frontend│ │ Backend  │
     │  Nginx  │ │ Flask App│
     └─────────┘ └──────────┘
             │
       ┌─────▼─────┐
       │ AWS RDS   │
       │ MySQL DB  │
       └───────────┘

🧰 Technologies Used

| Tool             | Purpose                                     |
| ---------------- | ------------------------------------------- |
| **Ansible**      | Infrastructure provisioning & configuration |
| **AWS**          | Cloud infrastructure (EC2, RDS, VPC)        |
| **Jenkins**      | CI/CD pipeline for automated deployment     |
| **GitHub**       | Source control and webhook integration      |
| **Python/Flask** | Backend application                         |
| **Nginx**        | Reverse proxy / frontend server             |
| **MySQL**        | Relational database via AWS RDS             |
| **Prometheus**   | Monitoring system                           |
| **Slack**        | Deployment notifications via webhook/email  |



📂 Folder Structure

ansible-aws-webapp/
├── Jenkinsfile
├── inventory/
│   └── aws_ec2.yaml
├── roles/
│   ├── nginx/
│   ├── flask/
│   └── mysql/
├── playbooks/
│   ├── ec2-create.yml
│   ├── deploy.yml
├── templates/
│   ├── nginx.conf.j2
│   └── app.service.j2
└── README.md
