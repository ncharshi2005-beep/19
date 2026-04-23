pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pulls code from your Git repository
                checkout scm 
            }
        }

        stage('Docker Build') {
            steps {
                // Builds the image using the Dockerfile in the root directory
                // We use 'bat' for Windows commands
                bat 'docker build -t my-jenkins-app:%BUILD_NUMBER% .'
            }
        }

        stage('Docker Verify') {
            steps {
                // Verify the image exists in the local registry
                bat 'docker images' 
            }
        }
    }

    post {
        success {
            echo 'Docker image built and verified successfully!' 
        }
    }
}
