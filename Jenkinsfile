pipeline {
    agent { label 'go' }

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
                
                // Si deseas generar un reporte JUnit en el futuro:
                // sh 'go test -v ./... | go-junit-report > report.xml'
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
            // publish test report (si lo generas con go-junit-report)
            // junit 'report.xml'
        }
    }
}
