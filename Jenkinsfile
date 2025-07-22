pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/mayankbishtt/cloudrun'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-flask-app")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("my-flask-app").run("-p 8080:8080")
                }
            }
        }
    }
}
