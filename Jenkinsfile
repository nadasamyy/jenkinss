pipeline {
    agent any  // Use any available agent to run the job

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the Git repository
                git branch: 'main', url: 'https://github.com/nadasamyy/jenkinss.git'
            }
        }

        stage('Run Script') {
            steps {
                // Make the script executable and run it
                sh 'chmod +x run_script.sh'   // Give execute permissions to the script
                sh './run_script.sh'           // Execute the script
            }
        }
    }

    post {
        success {
            echo 'Build and script executed successfully!'
        }
        failure {
            echo 'Something went wrong.'
        }
    }
}
