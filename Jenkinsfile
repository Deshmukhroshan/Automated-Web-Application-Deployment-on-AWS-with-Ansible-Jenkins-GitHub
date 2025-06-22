pipeline {
    agent any

    environment {
        ANSIBLE_FORCE_COLOR = "1"
        PATH = "/usr/bin:/usr/local/bin:$PATH"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/ansible-aws-phase1.git'
            }
        }

        stage('Provision EC2') {
            steps {
                sh 'ansible-playbook ec2-create.yml'
            }
        }

        stage('Update Inventory') {
            steps {
                script {
                    def ip = sh(
                        script: "ansible-playbook ec2-create.yml | grep 'EC2 Public IP:' | awk '{print \$4}'",
                        returnStdout: true
                    ).trim()
                    writeFile file: 'inventory.ini', text: "[web]\\n${ip} ansible_user=ec2-user ansible_ssh_private_key_file=/var/lib/jenkins/.ssh/your-key.pem"
                }
            }
        }

        stage('Install Apache') {
            steps {
                sh 'ansible-playbook -i inventory.ini apache-install.yml'
            }
        }
    }
}
