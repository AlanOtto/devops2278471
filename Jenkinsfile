pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Configurar o repositório Jenkins
                    sh 'sudo sh -c "echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list"'

                    // Baixar e adicionar a chave do Jenkins
                    sh 'sudo apt-key adv --fetch-keys https://pkg.jenkins.io/debian/jenkins.io.key'

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
