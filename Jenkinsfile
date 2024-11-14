pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Ensure Docker is available in the environment
                    if (docker.available()) {
                        // Build Docker image based on Dockerfile in Branch 1
                        docker.build("my-flask-app")
                    } else {
                        error "Docker is not available in the environment."
                    }
                }
            }
        }
        stage('Run Application') {
            steps {
                script {
                    // Run the Flask application in a Docker container
                    if (docker.available()) {
                        docker.image("my-flask-app").run('-p 5000:5000')
                    } else {
                        error "Docker is not available in the environment."
                    }
                }
            }
        }
    }
}
