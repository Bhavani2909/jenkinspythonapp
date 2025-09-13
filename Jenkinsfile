pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/<your-username>/<repo-name>.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("python-jenkins-app")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker run -d -p 5000:5000 --name python-app python-jenkins-app'
                }
            }
        }
    }

    post {
        always {
            sh 'docker ps -a'
        }
    }
}

