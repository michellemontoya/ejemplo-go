pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { 
                git url: 'https://github.com/michellemontoya/ejemplo-go.git', branch: 'main'
            }
            
        }
        stage('Build') {
            steps { sh 'go build .' }
        }
        stage('Test') {
            steps { sh 'go test ./...' }
        }
    }
}
