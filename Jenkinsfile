pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'nodejs-app'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/teegee26/app-nodejs.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(env.DOCKER_IMAGE)
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("${env.DOCKER_IMAGE}:latest").run("-p 3000:3000")
                }
            }
        }
    }
}
