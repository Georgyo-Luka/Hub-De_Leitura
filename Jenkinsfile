pipeline {
    agent any

    /* Limpa o workspace ANTES de iniciar qualquer estágio */
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
                echo "🔨 Rodando build..."
                sh """
                    echo 'executando build'
                    # coloque seu comando real aqui
                    # ex: mvn clean package
                """
            }
        }

        stage('Tests') {
            steps {
                echo "🧪 Rodando testes..."
                sh """
                    echo 'rodando testes'
                    # coloque seu comando real aqui
                    # ex: mvn test
                """
            }
        }

        stage('Deploy') {
            steps {
                echo "🚀 Fazendo deploy..."
                sh """
                    echo 'simulando deploy'
                    # coloque seu comando real aqui
                    # ex: scp target/app.jar servidor:/apps/
                """
            }
        }
    }

    post {
        always {
            echo "🧹 Limpando workspace depois do pipeline..."
            cleanWs()
        }
    }
}
