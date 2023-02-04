pipeline {
    agent any
    
    stages {
        stage('CloneRepo') {
            steps {
                git branch: 'main', url: 'https://github.com/mohammedashiqu/jenkins-docker.git'
            }
        }

    stages {
        stage('Build docker image') {
            steps {
                sh 'docker build -t ashiqummathoor/newapp:latest .
            }
        }
    }
}
