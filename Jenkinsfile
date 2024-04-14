pipeline {
    agent any

    stages {
        stage('Deploy to K8s') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6C81F32C212FDB38DD7C3BFC17201E89.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
         stage('Verify Deploymnet') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6C81F32C212FDB38DD7C3BFC17201E89.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl svc all -n webapps"
                }
            }
        }
    }
}
