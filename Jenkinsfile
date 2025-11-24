pipeline {
    agent any

    options {
        deleteDir()
    }

    stages {

        stage('Checkout') {
            steps {
                echo "⛰️ Fazendo checkout do repositório..."
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh """
                    echo '🔨 executando build'
                """
            }
        }

        stage('Tests') {
            steps {
                sh """
                    echo '🧪 rodando testes'
                """
            }
        }

        stage('Deploy') {
            steps {
                sh """
                    echo '🚀 simulando deploy'
                """
            }
        }
    }

    post {
        always {
            echo "🧹 Limpando workspace..."
            cleanWs()
        }
    }
}
