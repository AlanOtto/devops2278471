pipeline {
    agent any
    stages {        
        stage('Conferindo versão de dependencias') {
            steps {
                script {
                    sh 'npm --version'
                    sh 'docker --version'
                    sh 'docker-compose --version'
                }
            }
        }
        stage('Construindo Repository')
            steps {
                script {
                    sh 'npm install'
                }
            }
        stage('Teste Repository') {
            steps {
                script {
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
        stage('Parar o Projeto') {
            steps {
                sh 'docker-compose down'
            }
        }
    }
}