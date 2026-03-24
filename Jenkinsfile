pipeline {
  agent any

  stages {
    stage('Build Docker Image') {
      steps {
        sh 'docker build -t snake-game .'
      }
    }

    stage('Run Container') {
      steps {
        sh 'docker run -d -p 8086:80 snake-game'
      }
    }
  }
}
