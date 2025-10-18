pipeline {
    agent any

    stages {
        stage('git-checkout') {
            steps {
                git 'https://github.com/Manthan0421/project2.git'
            }
        }

        stage('terraform-init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('terraform-plan') {
            steps {
                sh 'terraform plan'
            }
        }

        stage('terraform-apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }
}
