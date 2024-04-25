pipeline {
    agent any
    stages {
        stage('Build and Run Backend') {
            steps {
                // Change directory to backend
                dir('backend') {
                    sh 'apt-get install -y nodejs'
                    sh 'apt-get install -y npm'
                    sh 'node --version'
                    // Install dependencies
                    sh 'npm install'
                    // Start the backend server
                    sh 'npm start'
                }
            }
        }
        stage('Build and Run Frontend') {
            steps {
                // Change directory to frontend/e-commerce
                dir('frontend/e-commerce') {
                    // Install dependencies
                    sh 'npm install'
                    // Start the frontend server
                    sh 'npm start'
                }
            }
        }
    }
}
