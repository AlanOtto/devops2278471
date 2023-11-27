pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Criar um diretório temporário para o GPG dentro do workspace
                    def gpgTempDir = "${WORKSPACE}/jenkins-gpg"
                    sh "mkdir -p $gpgTempDir"

                    // Ajustar as permissões do diretório temporário
                    sh "chmod 777 $gpgTempDir"

                    // Configurar o ambiente do GPG
                    sh 'export GNUPGHOME=$gpgTempDir'

                    // Configurar o repositório Jenkins e baixar a chave
                    sh 'echo deb [signed-by=/usr/share/keyrings/jenkins-archive-keyring.gpg] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list'

                    // Mudar para o diretório temporário
                    sh "cd $gpgTempDir"

                    // Remover a chave GPG se existir
                    sh 'rm -f jenkins-archive-keyring.gpg'

                    // Baixar a chave do Jenkins
                    sh 'curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | gpg --batch --dearmor -o jenkins-archive-keyring.gpg'

                    // Ajustar as permissões da chave GPG
                    sh "chmod 600 jenkins-archive-keyring.gpg"
                    sh "sudo chown jenkins:jenkins jenkins-archive-keyring.gpg"

                    // Mover a chave para o diretório de keyrings
                    sh "sudo mv jenkins-archive-keyring.gpg /usr/share/keyrings/"

                    // Voltar para o diretório de trabalho original
                    sh "cd -"

                    // Atualizar o índice do pacote
                    sh 'sudo -E apt-get update'

                    // Instalar dependências
                    sh 'sudo -E apt-get install -y default-jdk docker.io docker-compose'

                    // Verificar as versões
                    sh 'java --version'
                    sh 'docker version'
                    sh 'docker-compose version'

                    // Remover o diretório temporário
                    sh "rm -rf $gpgTempDir"
                }
            }
        }
    }
}
