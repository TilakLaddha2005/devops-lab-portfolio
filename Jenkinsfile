pipeline {
    agent any

    stages {
        stage('Verify') {
            steps {
                echo 'Checking files...'
                bat 'dir'
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
                bat 'docker rm -f portfolio-container || exit 0'
                bat 'docker run -d --name portfolio-container -p 8081:80 portfolio-app'
            }
        }
    }
}
