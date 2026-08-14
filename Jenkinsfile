pipeline {

    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/your-repo.git'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t devops-app:v1 .'
            }
        }

        stage('Terraform') {
            steps {
                dir('terraform') {
                    sh 'terraform init'
                    sh 'terraform apply -auto-approve'
                }
            }
        }

        stage('Deploy K8s') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}