pipeline {
  agent any

  stages {

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t snake-game .'
      }
    }

    stage('Stop Old Container') {
      steps {
        sh 'docker rm -f snake-container || true'
      }
    }

    stage('Run Container') {
      steps {
        sh 'docker run -d -p 8086:80 --name snake-container snake-game'
      }
    }

  }
}
