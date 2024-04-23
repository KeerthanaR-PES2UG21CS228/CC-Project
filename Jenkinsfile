pipeline {
    agent any

    stages {
        stage('Install Node.js and npm') {
            steps {
                script {
                    // Install Node.js and npm
                    sh 'curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -'
                    sh 'apt-get install -y nodejs'
                }
            }
        }
        
        stage('Build and Run Backend') {
            steps {
                dir('backend') {
                    // Navigate to the backend directory
                    sh 'npm install'
                    sh 'npm start &'
                }
            }
        }

        stage('Build and Run Frontend') {
            steps {
                dir('frontend/e-commerce') {
                    // Navigate to the frontend directory
                    sh 'npm install'
                    sh 'npm start &'
                }
            }
        }
    }
}
