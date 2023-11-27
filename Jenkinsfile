pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'sudo -E apt-get update && sudo -E apt-get install -y default-jdk docker.io docker-compose'

                    sh 'java --version'
                    sh 'docker version'
                    sh 'docker-compose version'
                }
            }
        }
    }
}
