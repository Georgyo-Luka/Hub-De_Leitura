pipeline {
    agent any

    options {
        deleteDir() // limpa o workspace antes de tudo
    }

    stages {

        stage('Checkout') {
            steps {
                echo "⛰️ Fazendo checkout do repositório..."

                git(
                    url: 'https://github.com/Georgyo-Luka/Hub-De_Leitura',
                    branch: 'main'
                )
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
