pipeline {
    agent any

    environment {
        IMAGE_NAME = "newImage"
        CONTAINER_NAME = "newImageContainer"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mayankbishtt/cloudrun'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "Building Docker image with tag: $IMAGE_NAME"
                    sh "docker build -t $IMAGE_NAME ."
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    echo "Running container named: $CONTAINER_NAME"
                    sh "docker rm -f $CONTAINER_NAME || true"
                    sh "docker run -d -p 8080:8080 --name $CONTAINER_NAME $IMAGE_NAME"
                }
            }
        }
    }
}
