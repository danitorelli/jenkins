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
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
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
