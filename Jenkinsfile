pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                kubeconfig(credentialsId: 'k8-tkn', serverUrl: 'https://B9547621C1C2F5C00E132453436EA758.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                kubeconfig(credentialsId: 'k8-tkn', serverUrl: 'https://B9547621C1C2F5C00E132453436EA758.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
