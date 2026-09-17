pipeline {

    agent {
        label 'agent1'
    }

    environment {
        IMAGE_NAME = "snake-game"
        CONTAINER_NAME = "snake-container"
        PORT = "8080"
    }

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/soundarya21112004/snake-game.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8085:80 --name snake-container snake-game'
            }
        }

    }

    post {

        success {
            echo 'Snake Game deployed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

    }
}
