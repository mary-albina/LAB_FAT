pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mary-albina/LAB_FAT.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t travel-app:latest .'
                }
            }
        }

        stage('K8s Deployment') {
            steps {
                script {
                    sh 'kubectl apply -f k8s/deployment.yaml'
                }
            }
        }

        stage('Verify') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get services'
            }
        }
    }
}
