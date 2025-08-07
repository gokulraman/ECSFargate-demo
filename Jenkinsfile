pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = 'docker-hub'
        IMAGE_NAME = 'gokulraman/dev-repo'
        IMAGE_TAG = 'flaskapp'
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

    //post {
        //always {
            //cleanWs()
        //}
    //}
}
