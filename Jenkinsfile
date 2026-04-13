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
                // We use --kubeconfig to ensure Jenkins finds the cluster
                // Note: Replace 'batch1.VITUNIVERSITY' with your actual username if different
                bat 'kubectl apply -f k8s/deployment.yaml --kubeconfig=C:/Users/batch1.VITUNIVERSITY/.kube/config --validate=false'
            }
        }
        stage('Verify') {
            steps {
                bat 'kubectl get pods --kubeconfig=C:/Users/batch1.VITUNIVERSITY/.kube/config'
            }
        }
    }
}
