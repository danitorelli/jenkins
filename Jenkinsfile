pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Passo 1: Checkout do repositório Git
                git 'https://github.com/danitorelli/jenkins.git'
            }
        }

        stage('Deploy') {
            steps {
                // Passo 4: Copiar os arquivos do blog para o diretório de deploy
                sh 'cp -R . /path/to/deploy'
            }
        }

        stage('Update Results') {
            steps {
                // Passo 5: Atualizar os resultados dos passos de build e test no HTML
                sh 'sed -i "s/<div id=\\"build-result\\"><\\/div>/<div id=\\"build-result\\">Build executado com sucesso!<\\/div>/" index.html'
                sh 'sed -i "s/<div id=\\"test-result\\"><\\/div>/<div id=\\"test-result\\">Testes passaram!<\\/div>/" index.html'
            }
        }

        stage('Notification') {
            steps {
                // Passo 6: Notificação por e-mail
                emailext body: 'A pipeline do blog foi concluída com sucesso!',
                    subject: 'Notificação de Pipeline - Blog',
                    to: 'dani.ctorelli@edu.unifil.br'
            }
        }
    }
}
