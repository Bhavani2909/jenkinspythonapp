pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Bhavani2909/jenkinspythonapp.git', branch: 'main', credentialsId: 'J'
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


