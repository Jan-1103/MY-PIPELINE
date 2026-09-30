pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                echo 'Building actual Docker image...'
                sh 'docker build -t my-demo-app:latest .'
            }
        }
        stage('Run Container') {
            steps {
                echo 'Running the container...'
                sh 'docker stop running-app || true'
                sh 'docker rm running-app || true'
                sh 'docker run -d -p 8080:8080 --name running-app my-demo-app:latest'
            }
        }
    }
}