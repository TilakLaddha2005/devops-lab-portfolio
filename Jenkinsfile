pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Docker Build') {
            steps {
                echo 'Building Docker Image...'
                bat 'docker build -t portfolio-app .'
            }
        }
        stage('Docker Run') {
            steps {
                echo 'Starting Docker Container...'
                // Removes old container if it exists to avoid port conflicts
                bat 'docker rm -f portfolio-container || true'
                bat 'docker run -d --name portfolio-container -p 8081:80 portfolio-app'
            }
        }
    }
}