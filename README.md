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
