pipeline {
    agent any
    stages {
        stage('Create build output') {
            steps {
                // Make the output directory.
                sh "mkdir -p output"

                // Write a useful file, which is needed to be archived.
                writeFile file: "output/usefulfile.txt", text: "This file is useful, need to archive it."

                // Write a useless file, which is not needed to be archived.
                writeFile file: "output/uselessfile.md", text: "This file is useless, no need to archive it."
            }
        }

        stage('Archive build output') {
            steps {
                // Archive the build output artifacts.
                archiveArtifacts artifacts: 'output/*.txt', excludes: 'output/*.md'
            }
        }

        stage('Test NodeGoat Repository') {
            steps {
                // Add your testing steps for the NodeGoat repository.
                // For example, you can clone the repository and run tests.
                script {
                    git url: 'https://github.com/AlanOtto/devops2278471.git'
                    sh 'npm install'  // Assuming NodeGoat is a Node.js project
                    sh 'npm test'     // Run tests
                }
            }
        }
    }
}
