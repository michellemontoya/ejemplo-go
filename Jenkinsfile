pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { git 'https://github.com/michellemontoya/ejemplo-go.git' }
        }
        stage('Build') {
            steps { sh 'go build .' }
        }
        stage('Test') {
            steps { sh 'go test ./...' }
        }
    }
}
