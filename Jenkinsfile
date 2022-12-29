pipeline{
    agent any {
    stage('Git Checkout'){
        git 'https://github.com/ramakrishna8254/helm-helloworld-srk.git'
    }
        stage('Build Docker Image') {
            steps {
                script {
                  sh 'docker build -t devopshint/nodejsapp-1.0:latest .'
                }
            }
        }
        stage('Deploy Docker Image') {
            steps {
                script {
                 withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                    sh 'docker login -u devopshint -p ${dockerhubpwd}'
                 }  
                 sh 'docker push devopshint/nodejsapp-1.0:latest'
                }
            }
        }
   }
}    
