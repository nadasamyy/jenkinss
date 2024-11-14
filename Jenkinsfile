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
                    sh 'start python hello.py'  // Use 'start' for Windows to run the app
                }
            }
        }
    }
}
