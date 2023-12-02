pipeline {
    agent any

    tools {nodejs 'node'}

    stages {
        stage('test'){
            steps{
                sh 'npm install'
                sh 'npm test'
            }
        }
        stage('build') {
            steps {
                sh 'docker-compose build' 
            }
        }
         stage('up') {
            steps {
                sh 'docker-compose up'  
            }
        }
}
}