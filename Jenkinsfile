pipeline {
    agent any

    environment {
        ANSIBLE_FORCE_COLOR = "1"
        PATH = "/usr/bin:/usr/local/bin:$PATH"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/Deshmukhroshan/Automated-Web-Application-Deployment-on-AWS-with-Ansible-Jenkins-GitHub.git'
            }
        }

        stage('Provision EC2') {
            steps {
                script {
                    // Run ansible-playbook and capture the IP from debug output
                    def output = sh(
                        script: "ansible-playbook ec2-create.yml",
                        returnStdout: true
                    ).trim()

                    // Extract the IP from output (look for debug line)
                    def match = output =~ /EC2 Public IP: ([0-9.]+)/
                    if (match) {
                        env.EC2_PUBLIC_IP = match[0][1]
                        echo "Extracted EC2 IP: ${env.EC2_PUBLIC_IP}"
                    } else {
                        error("Failed to extract EC2 public IP from playbook output")
                    }
                }
            }
        }

        stage('Update Inventory') {
            steps {
                writeFile file: 'inventory.ini',
                    text: "[web]\n${env.EC2_PUBLIC_IP} ansible_user=ec2-user ansible_ssh_private_key_file=/var/lib/jenkins/.ssh/your-key.pem"
            }
        }

        stage('Install Apache') {
            steps {
                sh 'ansible-playbook -i inventory.ini apache-install.yml'
            }
        }
    }
}
