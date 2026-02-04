pipeline {
	agent any
	environment {
		DOCKERHUB_CRED=credentials('dockerhub')
		IMAGE_NAME="vishwasvishu123/myapp"
	}
	
	stages {
		stage('checkout') {
			steps {
				git url:'https://github.com/Darshan262003/v2.git', branch:'main' 
			}
		}
		
		stage('Build Docker Image') {
			steps {
				script {
					dockerImage=docker.build("${IMAGE_NAME}:latest")
				}
			}
		}
		
		stage('Push to DockerHub') {
			steps {
				script {
					docker.withRegistry('https://index.docker.io/v1/','dockerhub') {
             docker.push()
}
}
}
}
}
}
