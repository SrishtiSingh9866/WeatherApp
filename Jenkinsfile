pipeline {
    agent any

    environment {
        IMAGE_NAME = 'weatherapp'
        CONTAINER_NAME = 'weatherapp-container'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/SrishtiSingh9866/WeatherApp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop & remove old container if exists
                    sh "docker rm -f ${CONTAINER_NAME} || true"

                    // Run new container
                    sh "docker run -d --name ${CONTAINER_NAME} -p 3000:80 ${IMAGE_NAME}"
                }
            }
        }
    }
}
