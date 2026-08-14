pipeline {
    agent any

    environment {
        KUBECONFIG = 'C:\\Users\\Ankit Kumar\\.kube\\config'
    }

    stages {

        stage('Build Docker Image') {
            steps {
                bat "docker build -t devops-app:${BUILD_NUMBER} ."
            }
        }

        stage('Update Deployment') {
            steps {
                bat "kubectl set image deployment/devops-app devops-app=devops-app:${BUILD_NUMBER}"
            }
        }

        stage('Verify') {
            steps {
                bat 'kubectl rollout status deployment/devops-app'
            }
        }
    }
}