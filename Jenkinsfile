pipeline {
  agent { label 'aws'}
    stages {
        stage('Preparation') {
            steps {
                git branch:'master', url: 'https://github.com/Yomna521/mean-stack-docker.git'
            }
        }
        stage('Build') {
            steps {
 withCredentials([usernamePassword(credentialsId:"dockerhub",usernameVariable:"username",passwordVariable:"pass")]){
                sh 'docker build . -t ${username}/mean-stack:tagname'
                sh 'docker login -u ${username} -p ${pass}'
                sh 'docker push ${username}/mean-stack:tagname'
                }
            }
        }  
        stage ('deploy'){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerhub",usernameVariable:"username",passwordVariable:"pass")]){
                
                sh 'docker run -p 8000:8000 -d ${username}/mean-stack:tagname'
                }
            }

        }
            
    }
}
