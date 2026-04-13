pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t travel-app:latest .'
            }
        }

        stage('K8s Deployment') {
            steps {
                // Added --validate=false to bypass the server-side error
                bat 'kubectl apply -f k8s/deployment.yaml --validate=false'
            }
        }

        stage('Verify') {
            steps {
                bat 'kubectl get pods'
                bat 'kubectl get services'
            }
        }
    }
}
