pipeline {
    agent { label 'agent3' }

    environment {
        GIT_URL = 'https://github.com/michellemontoya/ejemplo-go.git'
        GIT_BRANCH = 'main'
        GO_BIN = '/usr/local/go/bin/go'
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
                    def goVersion = sh(script: "${GO_BIN} version", returnStdout: true).trim()
                    echo "Go version: ${goVersion}"
                }
            }
        }

        stage('Build') {
            steps {
                sh '${GO_BIN} build .'
            }
        }

        stage('Test') {
            steps {
                sh '${GO_BIN} test -v ./...'
            }
        }

        stage('Clean') {
            steps {
                sh '${GO_BIN} clean -cache'
            }
        }
    }

    post {
        always {
            echo '✅ Pipeline completado (sin importar el resultado).'
        }
    }
}
