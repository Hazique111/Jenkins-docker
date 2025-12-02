pipeline {
    agent any

    environment {
        DOCKER_HUB = credentials('docker-hub-credential')
    }

    stages {
        stage('Git Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Hazique111/Jenkins-docker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t haziquekhan/my-app:latest .'
            }
        }

        stage('Docker Login') {
            steps {
                sh 'echo $DOCKER_HUB_PSW | docker login -u $DOCKER_HUB_USR --password-stdin'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push haziquekhan/my-app:latest'
            }
        }
    }
}
