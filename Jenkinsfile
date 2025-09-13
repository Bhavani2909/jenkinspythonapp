pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t myflaskapp:latest .'
            }
        }
        stage('Deploy Container') {
            steps {
                sh '''
                    sudo docker stop myflaskapp || true
                    sudo docker rm myflaskapp || true
                    sudo docker run -d --name myflaskapp -p 80:5000 myflaskapp:latest
                '''
            }
        }
    }

    post {
        always {
            sh 'sudo docker ps -a'
        }
    }
}



