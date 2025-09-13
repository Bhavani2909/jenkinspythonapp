pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build Docker Image') {
            steps { sh 'docker build -t myflaskapp:latest .' }
        }
        stage('Deploy Container') {
            steps {
                sh '''
                    docker stop myflaskapp || true
                    docker rm myflaskapp || true
                    docker run -d --name myflaskapp -p 80:5000 myflaskapp:latest
                '''
            }
        }
    }
    post {
        always { sh 'docker ps -a' }
    }
}




