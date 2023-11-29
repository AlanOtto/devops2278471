pipeline {
    agent any

    stages {
        stage('Install Docker') {
            steps {
                script {
                    sh 'npm install'
                    sh 'npm test'
                    // Instalação do Docker
                    sh 'sudo apt-get update'
                    sh 'sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common'
                    sh 'curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg'
                    sh 'echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null'
                    sh 'sudo apt-get update'
                    sh 'sudo apt-get install -y docker-ce docker-ce-cli containerd.io'
                }
            }
        }
    }
}
