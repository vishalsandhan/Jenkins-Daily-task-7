pipeline {
    agent any
    environment {
        IMAGE_NAME = 'flask-app'
        CONTAINER_NAME = 'flask-container'
    }
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/vishalsandhan/Jenkins-Daily-task-7.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh 'docker run -d -p 5000:5000 --name $CONTAINER_NAME $IMAGE_NAME'
                }
            }
        }
        stage('Clean Up') {
            steps {
                script {
                    sh 'docker stop $CONTAINER_NAME || true'
                    sh 'docker rm $CONTAINER_NAME || true'
                }
            }
        }
    }
}