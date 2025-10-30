pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
        AWS_DEFAULT_REGION    = 'ap-south-1'   // change if needed
    }

    stages {
        stage('git-checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Manthan0421/project2.git'
            }
        }

        stage('terraform-init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('terraform-plan') {
            steps {
                sh 'aws sts get-caller-identity'  // optional: confirm creds work
                sh 'terraform plan'
            }
        }

        stage('terraform-apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }

        stage('terraform-destroy') {
            steps {
                sh 'terraform destroy -auto-approve'
            }
        }
    }
}
