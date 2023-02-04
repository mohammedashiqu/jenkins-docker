pipeline {
    agent any
    environment {
		DOCKERHUB_CREDENTIALS=credentials('docker_hub_cred')
	}

    stages {
        stage('arun clone repo') {
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
	stage('update new image') {
            steps {
                sh 'sudo docker pull ashiqummathoor/mytestimage'
            }
        }
	stage('delete existing image') {
            steps {
                sh 'sudo docker stop app'
		sh 'sudo docker rm app'
		sh 'sudo docker rmi ashiqummathoor/mytestimage'
            }
        }
	stage('run new image') {
            steps {
                sh 'sudo docker run -d -p 1000:80 --name app ashiqummathoor/mytestimage'
            }
        }
	stage('update new image kubernetes') {
            steps {
                sh 'sudo kubectl replace --force -f /var/lib/jenkins/workspace/project'
            }
        }
    }
}
