pipeline {
    agent none
    stages {
        stage('Deploy') {
            agent any
            steps {
                withAWS(region: 'ap-southeast-2', credentials: 'aws-credential') {
                    sh "aws eks update-kubeconfig --name sd4650-devops-eks"
                    sh "kubectl apply -f mongodb.yaml"
                    sh "kubectl apply -f backend.yaml"
                    sh "kubectl apply -f frontend.yaml"
                }
            }
        }
    }
}