pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Adicionar a chave pública do Jenkins
                    sh 'wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | gpg --dearmor -o /tmp/jenkins-archive-keyring.gpg'

                    // Configurar o repositório Jenkins
                    sh 'echo "deb [signed-by=/tmp/jenkins-archive-keyring.gpg] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null'

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
