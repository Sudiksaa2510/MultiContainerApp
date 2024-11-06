pipeline {
    agent any

    environment {
        // Define environment variables if needed
        MY_VARIABLE = 'value'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                // Checkout the repository
                checkout scm
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    // Windows-compatible command to run docker-compose
                    bat 'echo "Starting Docker Compose..."'
                    bat 'docker-compose up -d'  // Run Docker Compose in detached mode
                    
                    // Optionally, to run it in the background (asynchronously) on Windows
                    // bat 'start docker-compose up -d'
                }
            }
        }

        stage('Post Build') {
            steps {
                script {
                    // Additional post-build actions like tests, cleanup, etc.
                    bat 'echo "Running post-build tasks..."'
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up after the build.'
            // Add any cleanup steps if needed
        }
    }
}
