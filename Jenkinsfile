pipeline{

    agent any

    stages {
        stage('Build') {
            steps {
                sh 'java --version'
                sh 'docker version'
                sh 'docker-compose version'       
            }
        }
    }
}