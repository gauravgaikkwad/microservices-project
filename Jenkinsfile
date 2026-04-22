pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-gaurav', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://2D0CE2D96BFB995819F06EBB24F56AC5.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-gaurav', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://2D0CE2D96BFB995819F06EBB24F56AC5.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
