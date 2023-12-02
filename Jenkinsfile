pipeline {
    agent any
    stages {        
        stage('Conferindo versão de dependencias') {
            steps {
                script {
                    sh 'docker --version'
                    sh 'npm --version'
                }
            }
        }
        stage('Teste NodeGoat Repository') {
            steps {
                script {
                    sh 'npm install'
                    sh 'npm test'
                }
            }
        }
        stage('build Projeto') {
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