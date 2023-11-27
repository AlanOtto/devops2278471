pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'java --version'
                    sh 'docker version'
                    sh 'docker-compose version'
                }
            }
        }
    }
}
