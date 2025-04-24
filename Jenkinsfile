pipeline {
    agent any
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
                    // Verificar si Go está instalado y en el PATH
                    def goVersion = sh(script: 'go version', returnStdout: true).trim()
                    echo "Go Version: ${goVersion}"
                }
            }
        }
        stage('Build') {
            steps {
                sh 'go build .'  // Compilar el proyecto
            }
        }
        stage('Test') {
            steps {
                sh 'go test -v ./...'  // Ejecutar pruebas Go
            }
        }
        stage('Clean') {
            steps {
                sh 'go clean -cache'  // Limpiar caché (opcional)
            }
        }
    }
    post {
        always {
            // Aquí puedes agregar otros pasos postejecución si es necesario
        }
    }
}
