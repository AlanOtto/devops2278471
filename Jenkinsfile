pipeline {
    agent any
    stages {
        stage('Clonar Repositório') {
            steps {
                // Comandos para clonar o repositório
                git 'https://github.com/AlanOtto/devops2278471.git'
            }
        }

        stage('Configurar e Testar') {
            steps {
                // Comandos para configurar e testar o projeto
                sh 'npm install'
                sh 'npm test'
            }
        }

        // Adicione mais stages conforme necessário
    }
}
