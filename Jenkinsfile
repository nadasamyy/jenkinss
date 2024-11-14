pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t myimage .'
                }
            }
        }
        stage('Run Application') {
            steps {
                script {
                    // Run the Flask app using python
                    sh 'python hello.py'  // Use 'python' instead of 'start' for Unix-like systems
                }
            }
        }
    }
}
