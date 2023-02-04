pipeline {
    agent any
    environment {
		DOCKERHUB_CREDENTIALS=credentials('docker_hub_cred')
	}

    stages {
        stage('clone repo') {
            steps {
                git branch: 'main', url: 'https://github.com/mohammedashiqu/jenkins-docker.git'
            }
        }
        stage('build image') {
            steps {
                sh 'sudo docker build . -t ashiqummathoor/mytestimage' 
            }
        }
        stage('Login to docker hub') {
            steps {
                sh 'sudo echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push to docker hub') {
            steps {
                sh 'sudo docker push ashiqummathoor/mytestimage'
            }
        }
    }
}
