pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'myflaskapp'
    }

    stages {
        stage('Build and Run') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'main') {
                        echo "Building and running Docker container for main branch"
                        
                        // Build the Docker image
                        sh '''
                        docker build -t ${DOCKER_IMAGE} .
                        '''

                        // Run the Docker container
                        sh '''
                        docker run -d -p 5000:5000 --name flask_app ${DOCKER_IMAGE}
                        '''
                    } else if (env.BRANCH_NAME == 'feature') {
                        echo "Running Flask application for feature branch"
                        
                        // Install dependencies and run Flask application directly
                        sh '''
                        python3 -m venv venv
                        source venv/bin/activate
                        pip install flask
                        python hello.py &
                        '''
                    } else {
                        error "Unsupported branch: ${env.BRANCH_NAME}"
                    }
                }
            }
        }
    }

    post {
        always {
            script {
                if (env.BRANCH_NAME == 'main') {
                    // Stop and remove the container to clean up
                    sh '''
                    docker stop flask_app || true
                    docker rm flask_app || true
                    '''
                }
            }
            echo "Clean-up completed"
        }
    }
}
