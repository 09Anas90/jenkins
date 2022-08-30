pipeline {
    agent any
environment {
    def kubeConfig="C:\\ProgramData\\Jenkins\\.jenkins\\.kube\\config"
    def getOs(){
    String osname = System.getProperty('os.name');
    if (osname.startsWith('Windows'))
        return 'windows';
    else if (osname.startsWith('Mac'))
        return 'macosx';
    else if (osname.contains('nux'))
        return 'linux';
    else
        throw new Exception("Unsupported os: ${osname}");
}
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
