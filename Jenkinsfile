pipeline {
    agent any

    stages {
        stage('Build docker image') {
            steps {
                sh 'sudo docker build -t myapp .'
            }
        }
    }
}
