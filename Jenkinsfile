pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Configurar o repositório Jenkins
                    sh 'echo deb [signed-by=/usr/share/keyrings/jenkins-archive-keyring.gpg] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list'

                    // Baixar a chave do Jenkins e adicioná-la ao sistema
                    sh 'curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | gpg --batch --dearmor -o /usr/share/keyrings/jenkins-archive-keyring.gpg'

                    // Atualizar o índice do pacote
                    sh 'sudo -E apt-get update'

                    // Instalar dependências
                    sh 'sudo -E apt-get install -y default-jdk docker.io docker-compose'

                    // Verificar as versões
                    sh 'java --version'
                    sh 'docker version'
                    sh 'docker-compose version'
                }
            }
        }
    }
}
