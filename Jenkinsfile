pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/Ankit-0395/devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-app:v1 .'
            }
        }

        stage('Load Image To Minikube') {
            steps {
                bat 'minikube image load devops-app:v1'
            }
        }

        stage('Deploy Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
}