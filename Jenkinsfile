pipeline {
    agent any
    environment {
        GIT_URL = 'https://github.com/michellemontoya/ejemplo-go.git'
        GIT_BRANCH = 'main'
    }
    stages {
        stage('Checkout') {
            steps {
                // Haciendo checkout del repositorio
                git url: "${GIT_URL}", branch: "${GIT_BRANCH}"
            }
        }
        stage('Build') {
            steps {
                // Construcción del proyecto Go
                sh 'go build .'
            }
        }
        stage('Test') {
            steps {
                // Ejecutar las pruebas Go
                sh 'go test -v ./...'  // -v para salida detallada
            }
        }
        stage('Clean') {
            steps {
                // Limpiar caché (opcional)
                sh 'go clean -cache'
            }
        }
    }
    post {
        always {
            // Publicar los resultados de las pruebas si están disponibles en formato XML
            junit '**/TEST-*.xml'  // Si tienes archivos XML generados por las pruebas
        }
    }
}
