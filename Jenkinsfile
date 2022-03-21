pipeline {
    agent { label '1' }

    environment {
        AWS_ACCESS_KEY_ID        = credentials('TERRAFORM_AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY    = credentials('TERRAFORM_AWS_SECRET_ACCESS_KEY')
    }

    tools {
        terraform 'Terraform'
    }

    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', credentialsId: 'github-ssh', url: 'git@github.com:Vladkarok/terraform-geocit-aws.git'
            }
        }    
        stage('Terraform init') {
            steps{
                sh 'terraform init'
            }
        }
        stage('Terraform apply') {
            steps{
                sh 'terraform apply -auto-approve'
            }
        }
    }
}


