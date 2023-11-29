pipeline {
    agent any

    stages {
        stage('Install Docker and Jenkins') {
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

                    // Importa a chave GPG do Jenkins
                    sh 'wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo gpg --dearmor -o /usr/share/keyrings/jenkins-archive-keyring.gpg'
                    sh 'echo "deb [signed-by=/usr/share/keyrings/jenkins-archive-keyring.gpg] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null'

                    // Atualiza a lista de pacotes após adicionar o repositório Jenkins
                    sh 'sudo apt-get update'

                    // Instalação do Jenkins
                    sh 'sudo apt-get install -y jenkins'
                }
            }
        }
    }
}
