pipeline {
    agent any

    parameters {
        choice(
            name: 'ACTION',
            choices: ['plan', 'apply', 'destroy'],
            description: 'Select the Terraform action to perform'
        )
    }

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
        AWS_DEFAULT_REGION    = 'us-east-1'
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
            when {
                expression { params.ACTION == 'plan' }
            }
            steps {
                sh 'terraform plan'
            }
        }

        stage('terraform-apply') {
            when {
                expression { params.ACTION == 'apply' }
            }
            steps {
                sh 'terraform apply -auto-approve'
            }
        }

        stage('terraform-destroy') {
            when {
                expression { params.ACTION == 'destroy' }
            }
            steps {
                sh 'terraform destroy -auto-approve'
            }
        }
    }
}
