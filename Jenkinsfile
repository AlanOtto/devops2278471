pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {

                    sh 'wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -'

                    sh 'sudo -E apt-get update'

                    sh 'sudo -E apt-get install -y default-jdk docker.io docker-compose'

                    sh 'java --version'
                    sh 'docker version'
                    sh 'docker-compose version'
                }
            }
        }
    }
}
