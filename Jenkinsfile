pipeline {
    agent any

    stages {
        stage('Install Docker') {
            steps {
                script {
                    // Instalação do Docker
                    sh 'sudo apt-get update'
                    sh 'sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common'
                    sh 'curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg'
                    sh 'echo "deb [signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null'
                    sh 'sudo apt-get update'
                    sh 'sudo apt-get install -y docker-ce docker-ce-cli containerd.io'

                    // Adiciona o usuário do Jenkins ao grupo docker para permitir comandos docker sem sudo
                    sh 'sudo usermod -aG docker jenkins'
                }
            }
        }
    }
}
