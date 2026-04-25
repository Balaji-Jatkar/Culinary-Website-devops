pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code downloaded from Git'
            }
        }

        stage('Show Files') {
            steps {
                sh 'ls -la'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t frontend-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f frontend-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name frontend-container frontend-app'
            }
        }
    }
}