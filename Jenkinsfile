pipeline {
    agent any
    stages {
        stage('Terraform init')
            environment {
            AWS_ACCESS_KEYS = credentials('aws_cred')
            }
            steps {
                sh 'terraform init'   
            }        
        }
        stage('Terraform apply') {
            environment {
            AWS_ACCESS_KEYS = credentials('aws_cred')
            }
             steps {
                sh 'terraform apply --auto-approve'   
            }        
        }
         stage('Ansible run') {
           steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'Ansible', inventory: 'inventory', playbook: 'wordpress.yml', vaultCredentialsId: 'aws-key2'
                sh 'ls -la'   
            }
        }
}
