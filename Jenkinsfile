pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t devops-app:v1 .'
            }
        }

        stage('Deploy Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
                bat 'kubectl rollout restart deployment devops-app'
            }
        }

        stage('Verify') {
            steps {
                bat 'kubectl get pods'
                bat 'kubectl get svc'
            }
        }
    }
}