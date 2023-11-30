pipeline {
    agent any
    
    stages {
        stage('Check Versions') {
            steps {
                script {
                    def javaVersion = sh(script: 'java -version 2>&1 | grep version | awk \'{print $3}\'', returnStatus: true).trim()
                    
                    echo "Java Version: $javaVersion"
                    
                    if (javaVersion.startsWith("1.8")) {
                        echo "Java version is 1.8, which is the required version."
                    } else {
                        error "Java version is not 1.8. Please use Java 1.8 for this pipeline."
                    }
                }
            }
        }
        
        // Add more stages as needed for your pipeline
    }
}
