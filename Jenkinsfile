pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/YOURUSERNAME/YOURREPO.git'
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
    post {
        success { echo 'Website is live at http://localhost:8081' }
        failure { echo 'Something went wrong' }
    }
}
