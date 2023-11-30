pipeline {
    agent any
    
    stages {
        stage('Check Versions') {
            steps {
                script {
                    def javaVersion = sh(script: 'java -version 2>&1 | grep version | awk \'{print $3}\'', returnStatus: true).trim()
                    
                    echo "Java Version: $javaVersion"

                }
            }
        }
        
        // Add more stages as needed for your pipeline
    }
}
