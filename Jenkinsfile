pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B9547621C1C2F5C00E132453436EA758.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B9547621C1C2F5C00E132453436EA758.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
