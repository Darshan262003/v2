pipeline {
    agent any

    environment {
        IMAGE_NAME = "vishwasvishu123/new1"
        DOCKER_HUB=credentials('dockerhub')
    }

    stages {

        stage('checkout') {
            steps {
                git url: "https://github.com/Darshan262003/v2.git",
                    branch: "main"
            }
        }

        stage('build') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                        dockerImage.push()
                    }
                }
            }
            
        }
         
    }
}
