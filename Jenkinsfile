pipeline {
    agent any

    stages { 
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://EF12323FAC2213C9A344BABF8C675962.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://EF12323FAC2213C9A344BABF8C675962.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
