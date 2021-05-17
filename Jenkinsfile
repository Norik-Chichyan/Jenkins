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
                sh 'ansible-playbook -i workspace/wordpress_pipe/inventory --user=ubuntu --private-key=/var/lib/jenkins/.ssh/aws-key2.pem workspace/wordpress_pipe/wordpress.yml'
                sh 'ls -la'   
            }
         }
    }
    
}
