pipeline {
    agent {
        docker {
            image 'node:14' // Use a Node.js Docker image with npm pre-installed
        }
    }
    
    stages {
        stage('Build') {
            steps {
                // Navigate to the backend directory and install backend dependencies
                dir('backend') {
                    sh 'npm install'
                }
                
                // Navigate to the frontend/e-commerce directory and start the frontend server
                dir('frontend/e-commerce') {
                    sh 'npm install'
                    sh 'npm start &'
                }
            }
        }
    }
}
