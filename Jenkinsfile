pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://626D165FB633DE558E9CBB1F609B873A.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://626D165FB633DE558E9CBB1F609B873A.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
