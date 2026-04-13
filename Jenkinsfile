pipeline {
    agent any

    stages {
        // Removed the "Checkout" stage because Jenkins does this automatically
        
        stage('Build Docker Image') {
            steps {
                // Use 'bat' for Windows Jenkins environments
                bat 'docker build -t travel-app:latest .'
            }
        }

        stage('K8s Deployment') {
            steps {
                bat 'kubectl apply -f k8s/deployment.yaml'
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
