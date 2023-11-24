pipeline{

    agent any

    stages {
        stage('Build') {
            steps {
                sh 
                 java --version
                 docker version
                 docker-compose version                
            }
        }
    }
}