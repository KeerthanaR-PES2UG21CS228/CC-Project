pipeline {
    agent any

    stages {
        stage('Install Node.js and npm') {
            steps {
                script {
                    // Install Node.js and npm
                    sh 'curl -sL https://deb.nodesource.com/setup_14.x | bash -'
                    sh 'apt-get install -y nodejs'
                }
            }
        }
        
        stage('Install packages') {
            steps {
                script {
                    // Install packages using Docker
                    sh "docker run --user='jenkins' --rm -v `pwd`/backend:/app -w /app node npm install"
                    sh "docker run --user='jenkins' --rm -v `pwd`/frontend/e-commerce:/app -w /app node npm install"
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
