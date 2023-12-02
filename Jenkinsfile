pipeline {
    agent any
    //tools {
    //    nodejs 'node'
    //}
    stages {        
        stage('Update Packages') {
            steps {
                script {
                    sh '/usr/bin/apt-get update'
                }
            }
        }
        stage('Test NodeGoat Repository') {
            steps {
                script {
                    sh '/usr/bin/npm install'
                    sh '/usr/bin/npm test'
                }
            }
        }
    }
}