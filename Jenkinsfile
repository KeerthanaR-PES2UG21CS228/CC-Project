pipeline {
    agent any

    stages {
        stage('Install Node.js and npm') {
            steps {
                script {
                    // Install packages using Docker
                    sh "docker run --rm -v `pwd`:/app -w /app node:14-alpine npm install"
                }
            }
        }
        
        stage('Build and Run Backend') {
            steps {
                dir('backend') {
                    // Navigate to the backend directory
                    sh 'npm start &'
                }
            }
        }

        stage('Build and Run Frontend') {
            steps {
                dir('frontend/e-commerce') {
                    // Navigate to the frontend directory
                    sh 'npm start &'
                }
            }
        }
    }
}
