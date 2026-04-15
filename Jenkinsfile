pipeline {
    agent any

    stages {
        stage('Source Checkout') {
            steps {
                echo 'Pulling latest code from GitHub...'
                checkout scm
            }
        }

        stage('Quality Gate (Test)') {
            steps {
                echo 'Checking for all required pages...'
                // Verifies that your new labs.html is actually present before deploying
                bat 'if exist index.html (echo "Home exists") else (exit 1)'
                bat 'if exist labs.html (echo "Labs page exists") else (exit 1)'
                bat 'if exist contact.html (echo "Contact page exists") else (exit 1)'
            }
        }

        stage('Automated Deployment') {
            steps {
                echo 'Deploying full website to Local Server...'
                // This copies EVERY .html file to your public folder
                bat 'copy /Y *.html C:\\Users\\Public\\'
                echo 'All pages (Home, Labs, Contact) are now LIVE.'
            }
        }
    }

    post {
        always {
            echo 'Pipeline Execution Finished.'
        }
    }
}