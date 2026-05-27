pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/Siddu-009/ecommerce-devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ecommerce-frontend:v1 ./frontend'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop ecommerce-app || true'
                sh 'docker rm ecommerce-app || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name ecommerce-app ecommerce-frontend:v1'
            }
        }
    }
}
