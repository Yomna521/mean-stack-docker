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
        	step([$class: 'DockerComposeBuilder', dockerComposeFile: 'docker-compose.yml', option: [$class: 'StartAllServices'], useCustomDockerComposeFile: false])
          }
          } 
         	
        stage ('deploy'){
             steps {
       	echo 'Deploying....'
            }
    }
 }
}
