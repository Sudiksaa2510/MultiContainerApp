pipeline {
    agent any

    environment {
        // Define any environment variables you need here
        MY_VARIABLE = 'value'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                // Checkout the repository (including the Docker Compose file)
                checkout scm
            }
        }

        stage('Check Docker and Docker Compose') {
            steps {
                script {
                    // Ensure Docker is installed and running
                    bat 'docker --version'
                    bat 'docker-compose --version'
                }
            }
        }

        stage('Build and Deploy') {
            steps {
                script {
                    // Running docker-compose up in detached mode
                    bat 'echo "Starting Docker Compose..."'
                    bat 'docker-compose up -d'  // Start the services in detached mode
                }
            }
        }

        stage('Post Build') {
            steps {
                script {
                    // Additional post-build actions if needed
                    bat 'echo "Running post-build tasks..."'
                }
            }
        }
    }

    post {
        always {
            // Cleanup actions after the build is finished
            echo 'Cleaning up after the build.'
            // Optionally, stop and remove containers when the build finishes
            bat 'docker-compose down'  // Stop and remove containers
        }
    }
}
