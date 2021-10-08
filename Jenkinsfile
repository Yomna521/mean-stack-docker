pipeline {
	environment {
		registry = "yomna521/mean-stack"
		registryCredential = 'dockerhub_id'
		dockerImage1 = ''
		dockerimage2 = ''
		}
 agent any
	stages {
		stage('Cloning our Git') {
			steps {
			git 'https://github.com/Yomna521/mean-stack-docker.git'
			}
		}
		stage('Build') {
			steps{
				sh "cd angular-client && npm install"
				script {
				dockerImage1 = docker.build registry + ":$BUILD_NUMBER"
				}
				sh "cd .."
				sh "cd express-server && npm install"
				script {
				dockerImage2= docker.build registry + ":$BUILD_NUMBER"
				}
			}
		}
		stage('Deploy ') {
			steps{
				echo 'Deploying....'
				sh "cd .."
				sh "cd angular-client"
				script {
					docker.withRegistry( 'https://registry.example1.com', registryCredential ) {
					dockerImage1.push()
					}
				sh "cd .."
				sh "cd express-server"
				script {
					docker.withRegistry( 'https://registry.example2.com', registryCredential ) {
					dockerImage2.push()
					}
				}
				sh "cd .."
				sh "sudo docker-compose up"
				}
			}
		}
	}
