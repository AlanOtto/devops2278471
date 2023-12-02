pipeline {
    agent any
    stages {        
        stage('Update Packages') {
            steps {
                script {
                    sh 'docker --version'
                    sh 'npm --version'
                }
            }
        }
        stage('Test NodeGoat Repository') {
            steps {
                script {
                    sh 'npm install'
                    sh 'npm test'
                }
            }
        }
    }
}