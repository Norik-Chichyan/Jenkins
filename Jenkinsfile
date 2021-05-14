pipeline {
    agent any
    stages {
        stage('Terraform init') {
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
                sh 'ls -la'   
            }   
        }
        stage('Ansible run') {
           steps {
                ansiblePlaybook credentialsId: 'aws-cred-priv', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'inventory', playbook: 'wordpress.yml'
                sh 'ls -la'   
            }
        }
    }
}
