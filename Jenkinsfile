pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'docker-hub'
        IMAGE_NAME = 'gokularaman/flask-app'
        IMAGE_TAG = 'v1'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                      
                      sh" docker push ${IMAGE_NAME}:${IMAGE_TAG}"
                    }
                }
            }
        }
    }

    //post {
        //always {
            //cleanWs()
        //}
    //}
}
