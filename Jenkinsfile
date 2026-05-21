pipeline {

    agent {
        label 'agent1'
    }

    environment {
        IMAGE_NAME = "snake-game"
        CONTAINER_NAME = "snake-container"
        PORT = "8085"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/soundarya21112004/snake-game.git'
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
                sh 'docker run -d -p $PORT:80 --name $CONTAINER_NAME $IMAGE_NAME'
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