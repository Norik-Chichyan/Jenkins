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
            }        
        }
         stage('Ansible run') {
           steps {
                ansiblePlaybook installation: 'Ansible', inventory: '/wordpress_pipe/inventory', playbook: '/wordpress_pipe/wordpress.yml', vaultCredentialsId: 'aws-key2'
                sh 'ls -la'   
            }
         }
    }
    
}
