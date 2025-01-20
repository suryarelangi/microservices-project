pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-cred', namespace: 'micro', serverUrl: 'https://15293241636C3D99FDC86BDD9BDA7939.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-cred', namespace: 'micro', serverUrl: 'https://15293241636C3D99FDC86BDD9BDA7939.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n micro"
                }
            }
        }
    }
}
