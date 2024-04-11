pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://AF0A670E7CBC47692E3728A335E1B1F0.yl4.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl apply -f deployment-service.yml"
                   sleep 60
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: '', namespace: 'webapps', serverUrl: 'https://AF0A670E7CBC47692E3728A335E1B1F0.yl4.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
