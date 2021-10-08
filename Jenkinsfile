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
        	sh "docker-compose up"
          }
          } 
         	
        stage ('deploy'){
             steps {
       	echo 'Deploying....'
            }
    }
 }
}
