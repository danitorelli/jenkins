pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/danitorelli/jenkins.git'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                
                // Gerar número de versão baseado no BUILD_NUMBER
                def version = "1.0.${env.BUILD_NUMBER}"
                
                // Atualizar o arquivo index.html com o número de versão
                sh "sed -i 's/##VERSION##/${version}/' index.html"
            }
        }

        stage('Test') {
            steps {
                // Executar os testes
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                // Copiar arquivos para o diretório de implantação
                sh 'mkdir -p /path/to/deploy'
                sh 'cp index.html /path/to/deploy/'
                sh 'cp script.js /path/to/deploy/'
            }
        }

        stage('Notification') {
            steps {
                emailext body: 'A pipeline do blog foi concluída com sucesso!',
                    subject: "Notificação de Pipeline - Blog #${env.BUILD_NUMBER}",
                    to: 'dani.ctorelli@edu.unifil.br'
            }
        }
    }
}
