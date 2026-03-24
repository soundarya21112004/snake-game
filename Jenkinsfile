pipeline {
  agent any

  stages {

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t snake-game .'
      }
    }

    stage('Clean Old Containers') {
      steps {
        sh 'docker rm -f $(docker ps -aq) || true'
      }
    }

    stage('Run Container') {
      steps {
        sh 'docker run -d -p 8085:80 --name snake-container snake-game'
      }
    }

  }
}
