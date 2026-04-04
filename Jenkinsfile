pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main',
            credentialsId: 'github-creds',
            url: 'https://github.com/Balaji-Jatkar/Culinary-Website'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t culinary-website:latest .'
      }
    }

    stage('Run Container') {
      steps {
        sh 'docker stop culinary-website-app || true'
        sh 'docker rm culinary-website-app || true'
        sh 'docker run -d -p 3000:80 --name culinary-website-app culinary-website:latest'
      }
    }
  }

  post {
    success { echo 'Culinary Website is live on port 3000' }
    failure { echo 'Something went wrong - check logs' }
  }
}