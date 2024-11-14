pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t myimage .'
                }
            }
        }
        stage('Run Application') {
            steps {
                script {
                    // Use 'start' to run the application in the background on Windows
                    sh 'start python hello.py'
                }
            }
        }
    }
}
