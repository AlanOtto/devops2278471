pipeline {
    agent any
    stages {        
    stage('Update Packages') {
    steps {
        script {
            sh 'sudo apt-get update'
        }
    }
}

        stage('Install Node.js and npm') {
            steps {
                script {
                    // Install Node.js and npm
                    sh 'apt-get update && apt-get install -y nodejs npm'
                }
            }
        }

        stage('Test NodeGoat Repository') {
            steps {
                script {
                    git url: 'https://github.com/AlanOtto/devops2278471.git'
                    sh 'npm install'
                    sh 'npm test'
                }
            }
        }
    }
}