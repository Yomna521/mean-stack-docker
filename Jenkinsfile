pipeline {
  agent { label 'aws'}
    stages {
        stage('Preparation') {
            steps {
                sh "git clone https://github.com/Yomna521/mean-stack-docker.git'
            }
        }
        stage('Build') {
          steps {
            sh "cd mean-stack-docker"
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
