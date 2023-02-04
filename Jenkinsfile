pipeline {
    agent any

    stages {
        stage('Build docker image') {
            steps {
                dockerImage = docker.build("monishavasu/my-react-app:latest")
            }
        }
    }
}
