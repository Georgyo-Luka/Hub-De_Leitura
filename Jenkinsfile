pipeline {
    agent any

    tools {
        nodejs "Node18"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Instalar dependências') {
            steps {
                sh 'npm install'
            }
        }

        stage('Preparar Banco de Dados') {
            steps {
                sh 'npm run db'
            }
        }

        stage('Validar Start') {
            steps {
                sh '''
                    # Sobe a aplicação por alguns segundos para garantir que não quebra
                    npm start &
                    APP_PID=$!
                    sleep 5
                    kill $APP_PID
                '''
            }
        }

        stage('Testes (se existirem)') {
            steps {
                script {
                    if (fileExists('package.json') && sh(script: "grep -q jest package.json", returnStatus: true) == 0) {
                        sh 'npm test'
                    } else {
                        echo "Nenhum teste configurado."
                    }
                }
            }
        }

        stage('Build de Artefatos') {
    agent {
        docker {
            image 'node:18-bullseye'
            args '-u root'
        }
    }
    steps {
        sh '''
            apt-get update && apt-get install -y zip
            zip -r hub-de-leitura.zip .
        '''
    }
}
        }
    }

    post {
        success {
            echo "Pipeline finalizado com sucesso!"
            archiveArtifacts artifacts: 'hub-de-leitura.zip', fingerprint: true
        }
        failure {
            echo "Pipeline falhou."
        }
    }
}
