pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Criar um diretório temporário para o GPG
                    def gpgTempDir = '/tmp/jenkins-gpg'
                    sh "mkdir -p $gpgTempDir"

                    // Configurar o repositório Jenkins e baixar a chave
                    sh 'echo deb [signed-by=/usr/share/keyrings/jenkins-archive-keyring.gpg] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list'
                    sh "curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | gpg --dearmor -o $gpgTempDir/jenkins-archive-keyring.gpg"

                    // Ajustar as permissões do diretório GPG
                    sh "chmod -R 600 $gpgTempDir"
                    sh "sudo chown -R jenkins:jenkins $gpgTempDir"

                    // Mover a chave para o diretório final
                    sh "sudo mv $gpgTempDir/jenkins-archive-keyring.gpg /usr/share/keyrings/"

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
