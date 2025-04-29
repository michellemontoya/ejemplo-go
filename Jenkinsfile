pipeline {
    agent { label 'agent3' }

    environment {
        GIT_URL = 'https://github.com/michellemontoya/ejemplo-go.git'
        GIT_BRANCH = 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: "${GIT_URL}", branch: "${GIT_BRANCH}"
            }
        }

        stage('Check Go Installation') {
            steps {
                script {
                    // Verificar si Go está en el PATH
                    def goPath = sh(script: 'echo $PATH', returnStdout: true).trim()
                    echo "PATH: ${goPath}"

                    // Intentar obtener la versión de Go
                    def goVersion = sh(script: 'go version', returnStdout: true).trim()
                    echo "Go version: ${goVersion}"
                }
            }
        }

        stage('Build') {
            steps {
                sh 'go build .'
            }
        }

        stage('Test') {
            steps {
                sh 'go test -v ./...'
            }
        }

        stage('Clean') {
            steps {
                sh 'go clean -cache'
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline completado (sin importar el resultado).'
        }
    }
}
