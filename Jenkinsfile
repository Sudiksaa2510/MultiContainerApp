pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                git branch: 'master', url: 'https://github.com/Sudiksaa2510/MultiContainerApp.git'
            }
        }
        stage('Build and Deploy') {
            steps {
                script {
                    // Stop and remove any running containers (if any)
                    sh 'docker-compose down'
                    // Build and start the containers in detached mode
                    sh 'docker-compose up -d --build'
                }
            }
        }
    }
}
