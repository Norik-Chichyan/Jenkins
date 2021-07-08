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
        
        tage('run ansiblefor sv2') {
            environment {
            AWS_ACCESS_KEYS = credentials('aws_cred')
            }
             steps {
                sh 'ansiblePlaybook credentialsId: 'aws-cred-priv', disableHostKeyChecking: true, installation: 'Ansible', inventory: '/web-sv2/inv_sv2_aws_ec2.yml', playbook: 'web-sv2/sv2.yml''   
            }        
        }
    }
}
