pipeline {
    agent any

    tools {node 'Stages Alan'}

    stages {
        stage('Teste de Ambiente'){
            steps{
                sh 'npm install'
                sh 'npm test'
            }
        }
        stage('build') {
            steps {
                sh 'docker-compose build' 
                sh 'docker-compose up' 
            }
        }
        //stage('up') {
        //    steps {
        //        sh 'docker-compose up'  
        //    }
        //}
    }
}
