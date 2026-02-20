pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/prachiiyadv/devops-exam-app.git'
            }
        }

        stage('Build Backend Docker Image') {
            steps {
                sh 'docker build -t devops-backend ./backend'
            }
        }

        stage('Build Frontend Docker Image') {
            steps {
                sh 'docker build -t devops-frontend ./frontend'
            }
        }

        stage('Run Containers') {
            steps {
                sh 'docker stop devops-backend || true'
                sh 'docker rm devops-backend || true'
                sh 'docker run -d -p 3000:3000 --name devops-backend devops-backend'

                sh 'docker stop devops-frontend || true'
                sh 'docker rm devops-frontend || true'
                sh 'docker run -d -p 8081:80 --name devops-frontend devops-frontend'
            }
        }

    }
}
