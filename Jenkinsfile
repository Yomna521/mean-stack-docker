pipeline {
	environment {
		registry = "yomna521/mean-stack"
		registryCredential = 'dockerhub_id'
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
				sh "docker-compose up -d"
			}
		}
		stage('Deploy ') {
			steps{
				echo 'Deploying....'
				}
			}
		}
	}
