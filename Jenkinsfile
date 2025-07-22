pipeline {
    agent any

    environment {
        IMAGE_NAME = "newImage"
        CONTAINER_NAME = "newImageContainer"
        IMAGE_TAG = "newTag"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/mayankbishtt/cloudrun.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo "Building Docker image with tag: $IMAGE_NAME"
                    sh "docker build -t $IMAGE_NAME:$IMAGE_TAG ."
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    echo "Running container named: $CONTAINER_NAME"
                    sh "docker rm -f $CONTAINER_NAME || true"
                    sh "docker run -d -p 8080:8080 --name $CONTAINER_NAME $IMAGE_NAME:$IMAGE_TAG"
                }
            }
        }
    }
}
