pipeline {
    agent any
environment {
    def kubeConfig="C:\\ProgramData\\Jenkins\\.jenkins\\.kube\\config"
}
    stages {
        stage('Hello') {
            steps {
                script{
                    git branch: 'main',
                    url: 'https://github.com/09Anas90/jenkins.git'                    
                    bat 'cd app && docker build -t 09pineapple90/nodejs . && docker push 09pineapple90/nodejs'
                    bat "cd deployment && kubectl apply -f nodejs-ingress.yaml,nodejs.yaml,nodesvc.yaml --kubeconfig=$kubeConfig"
                    
                }
            }
        }
    }
}
