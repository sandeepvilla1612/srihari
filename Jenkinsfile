pipeline {
    agent any

    environment {
        IMAGE_NAME = 'my-python-app'
        CONTAINER_NAME = 'python-app'
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t $IMAGE_NAME ."
                }
            }
        }

        stage('Stop Existing Container') {
            steps {
                script {
                    sh "docker rm -f $CONTAINER_NAME || true"
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker run -d --name $CONTAINER_NAME -p 8000:8000 $IMAGE_NAME"
                }
            }
        }
    }
}
