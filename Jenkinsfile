pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/SrishtiSingh9866/WeatherApp'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("weatherapp")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    dockerImage.run("-p 80:80")
                }
            }
        }
    }
}
