pipeline {
	environment {
		registry = "yomna521/mean-stack"
		registryCredential = 'dockerhub_id'
		dockerImage = ''
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
				script {
				dockerImage = docker.build registry + ":$BUILD_NUMBER"
				}
			}
		}
		stage('Deploy ') {
			steps{
				echo 'Deploying....'
				script {
					docker.withRegistry( '', registryCredential ) {
					dockerImage.push()
					}
				}
				sh "docker-compose up"
				}
			}
		}
	}
