pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Vivek-vmk/jenkin-proj.git'
            }
        }

        stage('Stop Previous Containers') {
            steps {
                script {
                    sh 'docker-compose down || true'
                }
            }
        }

        stage('Build and Run with Docker Compose') {
            steps {
                script {
                    sh 'docker-compose up -d --build'
                }
            }
        }
    }

    post {
        success {
            echo 'App deployed successfully at port 8082!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
