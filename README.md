# Automated-Web-Application-Deployment-on-AWS-with-Ansible-Jenkins-GitHub
This project demonstrates a complete DevOps pipeline for deploying a multi-tier web application on AWS using Ansible, Jenkins, and GitHub. The solution automates the provisioning, configuration, and deployment of infrastructure and application components, integrating CI/CD workflows and infrastructure-as-code (IaC) principles.

🎯Key Objectives:
Provision AWS infrastructure (EC2 instances, RDS) using Ansible modules.

Deploy a multi-tier web application: Nginx (frontend), Flask (backend), MySQL (RDS).

Create modular, reusable roles using Ansible for configuration management.

Integrate with Jenkins for automated CI/CD pipeline.

Manage codebase and version control through GitHub.

Enable GitHub webhooks to trigger Jenkins on code updates.

Implement dynamic inventory with AWS EC2 instances.

Optional: Monitor instances using Node Exporter and Prometheus, with alerts via Slack.

🧱 Architecture Overview:

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

⚙️ Technologies Used:
Tool	                          Purpose

Ansible	                  Infrastructure provisioning & configuration
AWS	                      Cloud infrastructure(EC2, RDS, VPC)
Jenkins	                  CI/CD pipeline for automated deployment
GitHub	                  Source control and webhook integration
Python/Flask	            Backend application
Nginx	                    Reverse proxy / frontend server
MySQL	                    Relational database via AWS RDS
Prometheus                Monitoring
Slack                     Email	Notifications

🧩 Project Breakdown:
✅ Phase 1: Basic EC2 & Apache Deployment
Used Ansible to create EC2 instance.

Installed Apache and served a static HTML page.

✅ Phase 2: Jenkins CI/CD Integration
Setup Jenkins pipeline to pull code from GitHub.

Trigger Ansible playbooks on code push via webhooks.

✅ Phase 3: Multi-Tier Deployment with Roles
Created separate Ansible roles for Nginx, Flask, and MySQL.

Deployed backend app on EC2 and configured Nginx as a reverse proxy.

Used dynamic inventory to target EC2 instances by tags.

✅ Phase 4: Monitoring & Alerting (Optional)
Installed Node Exporter via Ansible.

Integrated Prometheus and Alertmanager for metrics and alerts.

Configured Slack notifications for deployment success/failure.

📂 Repo Structure (Sample)
lua
Copy
Edit
ansible-aws-webapp/
├── Jenkinsfile
├── inventory/
├── roles/
│   ├── nginx/
│   ├── flask/
│   └── mysql/
├── playbooks/
│   ├── ec2-create.yml
│   ├── deploy.yml
├── templates/
└── README.md
