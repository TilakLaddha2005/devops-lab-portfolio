pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Deploy to XAMPP') {
            steps {
                echo 'Deploying to C:\\xampp\\htdocs\\DEVOPS...'
                // Create directory if it doesn't exist
                bat 'if not exist "C:\\xampp\\htdocs\\DEVOPS" mkdir "C:\\xampp\\htdocs\\DEVOPS"'
                // Force copy all files to the subfolder
                bat 'copy /Y * "C:\\xampp\\htdocs\\DEVOPS\\"'
            }
        }
        stage('Docker Build') {
            steps {
                echo 'Building Docker Image...'
                // If this fails, make sure Docker Desktop is OPEN and GREEN
                bat 'docker build -t portfolio-app:v1 .'
            }
        }
        stage('Docker Run') {
            steps {
                echo 'Cleaning old container and starting new one...'
                bat 'docker rm -f portfolio-container || true'
                bat 'docker run -d --name portfolio-container -p 8082:80 portfolio-app:v1'
            }
        }
    }
}