pipeline {
    agent any
    stages {
        stage('Check Docker') {
            steps {
                // Check Docker version to ensure Docker is available
                sh 'docker --version'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image based on Dockerfile in Branch 1
                    docker.build("my-flask-app")
                }
            }
        }
        stage('Run Application') {
            steps {
                script {
                    // Run the Flask application in a Docker container
                    docker.image("my-flask-app").run('-p 5000:5000')
                }
            }
        }
    }
}
