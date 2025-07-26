pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'jagdish-cluster', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://79E835BE7A8E35B7C99360D56529C768.gr7.us-east-1.eks.amazonaws.com'
                ]]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'jagdish-cluster', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://79E835BE7A8E35B7C99360D56529C768.gr7.us-east-1.eks.amazonaws.com'
                ]]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
